<template>
    <div style="height: 500px; width: 800px">
        <div ref="cyto" class="cyto"></div>
    </div>
</template>
  
<script>
import cytoscape from 'cytoscape';
export default {
    data: () => ({
        cy: null
    }),
    mounted() {
        var cy = cytoscape({
            container: this.$refs.cyto, // container to render in

            elements: [
                // list of graph elements to start with
                {
                    // node a
                    data: { id: 'a' },
                },
                {
                    // node b
                    data: { id: 'b' },
                },
                {
                    // edge ab
                    data: { id: 'ab', source: 'a', target: 'b' },
                },
            ],

            style: [
                // the stylesheet for the graph
                {
                    selector: 'node',
                    style: {
                        'background-color': '#666',
                        label: 'data(id)',
                    },
                },
                {
                    selector: 'edge',
                    style: {
                        width: 3,
                        'line-color': '#ccc',
                        'target-arrow-color': '#ccc',
                        'target-arrow-shape': 'triangle',
                        'curve-style': 'bezier',
                    },
                },
            ],

            layout: {
                name: 'grid',
                rows: 1,
            },
        });
        this.cy = cy
    },
};
</script>
  
<style>
.cyto {
    height: 100%;
    width: 100%;
}
</style>
  