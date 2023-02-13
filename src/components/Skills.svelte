<script>
    // @ts-nocheck
    import { onMount } from "svelte";
    import Subheader from "./Subheader.svelte";
    export let skills;

    let container;
    
    onMount(() => {
        

        let observer = new IntersectionObserver(async (entries) => {
            if (entries[0].isIntersecting) {
                
                //console.log("started observing");
                observer.unobserve(container);

                const  {DataSet, Network}=await import('vis-network/standalone');
                
                Graph.__init(DataSet, Network);
            } else {
                //console.log("Done");
            }
        });
        observer.observe(container);

        const Graph = {
            nodes:null,
            edges:null,
            data:null,
            options: {
                // autoResize: false,
                // height:"70%",
                interaction: {
                    zoomView: false,
                },
            },
            __init: (DataSet, Network) => {

                Graph.nodes = new DataSet([]);
                Graph.edges = new DataSet([]);
                Graph.data = {
                    nodes: Graph.nodes,
                    edges: Graph.edges,
                };
                const network = new Network(container, Graph.data, Graph.options);
                Graph.formateDataset(skills);
            },
            delay: (ms) => {
                return new Promise((resolve) => setTimeout(resolve, ms));
            },
            randomInt: (min = 0, max) => {
                min = Math.ceil(min);
                max = Math.floor(max);
                return Math.floor(Math.random() * (max - min + 1)) + min;
            },
            formateDataset: async (data) => {
                let length = data.length;
                //console.log(length);
                let words = [];
                for (let index = 0; index < data.length; index++) {
                    const item = data[index];
                    if (index == 0) {
                        await Graph.addNode(item);
                        words = words.concat(item.title);
                        continue;
                    }
                    await Graph.addNode(item);
                    words = words.concat(item.title);
                    let sysedge = Graph.getEdge(words, item.title);

                    Graph.edges.add({
                        from: words[sysedge],
                        to: item.title,
                    });

                    await Graph.delay(400);
                }
            },
            getEdge: (words, title) => {
                let woid = Graph.randomInt(1, words.length) - 1;
                let id = words[woid];
                //console.log({ id, woid });
                if (id !== title) {
                    return woid;
                } else {
                    return Graph.getEdge(words, title);
                }
            },
            addNode: (item) => {
                return new Promise((resolve, reject) => {
                    Graph.nodes.add({
                        id: item.title,
                        label: item.title,
                        chosen: {
                            node: (values) => {
                                values.borderColor = "#ffbb00";
                            },
                        },
                        color: {
                            background: "#0A0A0A",
                            border: "#464D53",
                            hover: {
                                background: "#0A0A0A",
                                border: "#464D53",
                            },
                        },
                        font: {
                            color: "#F7F7F7",
                        },
                        shape: "box",
                        shapeProperties: {
                            borderDashes: [2, 1],
                            borderRadius: 6,
                            size: 20,
                            x: 0,
                            y: 0,
                        },
                        margin: 10,
                        imagePadding: 10,
                    });
                    resolve();
                });
            },
        };
        return ()=>{
            observer.unobserve(container);
        }
    });
</script>

<Subheader>Skills Set</Subheader>
<section class="wrapper" bind:this={container} />

<style>
    .wrapper {
        border: 0.2vmin solid var(--border);

        border-radius: 4px;
        background-image: radial-gradient(
            rgba(255, 255, 255, 0.2) 8%,
            transparent 8%
        );
        background-position: 0% 0%;
        background-size: 3vmin 3vmin;
        padding: 2vmin;
        transition: background-position 350ms ease;
        height: 60vh;
    }
    @media screen and (max-width: 1440px) {
        section {
            --sidePadding: 6%;
        }
    }
</style>
