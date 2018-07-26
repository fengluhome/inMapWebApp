<style scoped>
    .index {
        width: 100%;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        text-align: center;
    }
</style>
<template>
    <div class="index">
        <div class="map flex-1" ref="map" style="width:100%;height:100%"></div>
    </div>
</template>
<script>
    import inMap from "./../libs/inMap.min.js"
    import data from "./../data/point.json";
    export default {
        methods: {},
        mounted() {
            var inmap = new inMap.Map({
                id: this.$refs.map,
                skin: "Blueness",
                center: [105.403119, 38.028658],
                zoom: {
                    value: 5,
                    show: true,
                    max: 18,
                    min: 5
                },
            });
            //随机设置半径
            data.forEach(element => {
                element["style"] = {
                    size: Math.random() * 10
                }
            });
            var overlay = new inMap.PointOverlay({
                style: {
                    normal: {
                        backgroundColor: 'rgba(45, 140, 240, .5)',
                        borderWidth: 1,
                        borderColor: "rgba(0,131,238, 1)",
                        size: 10,
                    },
                },
                data: data,
            });
            inmap.add(overlay);
        }
    };
</script>