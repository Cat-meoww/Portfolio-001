<script>
    // @ts-nocheck
    import { onMount } from "svelte";
    import { DataSet, Network } from "vis-network/standalone";
    import Subheader from "./Subheader.svelte";
    //import "https://unpkg.com/vis-network/standalone/umd/vis-network.min.js";
    export let skills;

    //console.log(skills);
    // create a network
    let container;

    onMount(() => {
        // create an array with nodes
        const nodes = new DataSet([]);

        // create an array with edges
        const edges = new DataSet([]);

        const data = {
            nodes: nodes,
            edges: edges,
        };
        const options = {
            // autoResize: false,
            // height:"70%",
            interaction: {
                zoomView: false,
            },
        };
        let observer = new IntersectionObserver((entries) => {
            if (entries[0].isIntersecting) {
                //console.log("started observing");
                observer.unobserve(container);
                const network = new Network(container, data, options);
                Graph.__init();
            } else {
                //console.log("Done");
            }
        });
        observer.observe(container);

        let Graph = {
            __init: () => {
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

                    edges.add({
                        from: words[sysedge],
                        to: item.title,
                    });

                    await Graph.delay(300);
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
                    nodes.add({
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
