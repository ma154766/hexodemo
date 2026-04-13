---
title: echarts 注册中国地图
date: 2026-04-13 11:26:10
tags:
---


1.	组件引入
import * as myEcharts from 'echarts';

2.	下载geoJson https://datav.aliyun.com/portal/school/atlas/area_selector#&lat=30.332329214580188&lng=106.72278672066881&zoom=3.5

3.	使用
``` bash
        var series = [];

        series.push(
            {
                name: "线路",
                type: "lines",
                zlevel: 3,
                symbol: ["none", "arrow"],
                symbolSize: 0.1,
                effect: {
                    // show: true,
                    // period: 6,
                    // trailLength: 0,
                    // symbol: planePath,
                    // symbolSize: 15
                    show: true, //是否显示航线
                    period: 4, //箭头指向速度，值越小速度越快
                    trailLength: 0.02, //特效尾迹长度[0,1]值越大，尾迹越长重
                    symbol: 'arrow', //箭头图标
                    symbolSize: 5, //图标大小
                },
                lineStyle: {
                    normal: {
                        color: (params) => {
                            // params.dataIndex 是当前线的索引
                            return this.getRandomHexColor();
                        },
                        width: 1,
                        opacity: 0.6,
                        curveness: 0.2
                    }
                },
                data: [
                    {
                        fromName: "",
                        toName: "",
                        coords: [[90.89, 29.29], [80.05, 32.11]],
                        value: "",
                        ROUTE_NM: "",
                    }                
                ]
            },//线样式

            {
                name: '机场',
                type: "effectScatter",
                coordinateSystem: "geo",
                zlevel: 2,
                rippleEffect: {
                    brushType: "stroke"
                },
                label: {
                    normal: {
                        show: false,
                        position: "right",
                        formatter: "{@[2]}",
                        fontSize: 13
                    }
                },
                symbolSize: function (val) {
                    return 8;
                },
                // symbol: "image://data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABMAAAAVCAYAAACkCdXRAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyZpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNi1jMTQyIDc5LjE2MDkyNCwgMjAxNy8wNy8xMy0wMTowNjozOSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTggKFdpbmRvd3MpIiB4bXBNTTpJbnN0YW5jZUlEPSJ4bXAuaWlkOkEwMTQ2RjlEOEUyNjExRTg4QjdGRDQzMjFCMzE4RDA5IiB4bXBNTTpEb2N1bWVudElEPSJ4bXAuZGlkOkEwMTQ2RjlFOEUyNjExRTg4QjdGRDQzMjFCMzE4RDA5Ij4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6QTAxNDZGOUI4RTI2MTFFODhCN0ZENDMyMUIzMThEMDkiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6QTAxNDZGOUM4RTI2MTFFODhCN0ZENDMyMUIzMThEMDkiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz4G+FEkAAADeklEQVR42oRUW2wUVRj+5rK3ad3dsmyvWynSUEASYmliq4EHedIXU5Imhlu0Cb7w4AsPJvqgQiSkD2iiiQ9KSHiwGhOCWImAD2gTUNNaIYUCFtrSQrd7GXZnd/Y2cw7/TLuT7QX2T/7M+c/5zzfffzsC3uvEc6SNtIu0lTRBOkZ6o9KBnx5x1vIzQN4QZPFbQAi7ajxMcrs8pmGWzGyeMYMxztnX4Ph45aWVYCFRls6KHrmn9sX6oKx4Ks9sg5UMZB7GPyhp+j5usG7aWig7CBVhrhNk6TdfOLBTaV4noIoYegFPJmbz4HwDhWoDig6qJJ70hf2d1YA217Vg9NBXuHPkDIIdLV4i8IfQvzNYGeZbsuLua9u0Sfx897toCzTgZmwK44lp/Bv9H7NaAlFdResLYVzuOwHFtRi+XOOFd72/PR9LDZB52AajPJ1QmkKB1yLb8HZ7j+24I/ySw6bETPwzfwcddREHKJFL29+a5pCUiz7pJ3ZHJLzSVE9BHqvdUO+6p87h0tQoat0+bA21OmCSINqsykDT6Sj2nj+OZF6zso5CMpPmhnnFAuuSfe4+bzjg5VTv+ayKC5N/Yej+3+QnUI4icEnLi35gaAA34w8cu5DU8lTln60C+Cn5q5J+KzGDb/4bgsHNVUWoZG0XTxSs+x4LTCWKvHxQ6/LZjF5t2oJr+0/B71ZWgXXT2bIpoDa2CFr8rxv5YsDavND7KbqbtyCmpxBWAo6zms/g+uMJvLmxy7Y7G9qXgxmmxSxmMTMESRqiuO1WiOeWA6WLOnrPf4ZDvw4sJpxkY6ARjTV1KE8EK5nWjI6JS8if6I+SqQ+vfoetp9/Hvl9OwmCLufpi5BzG49P2+qM/zzg/2RXZbn9zj9UCZ+zLygkYIfTvs7PxomVcnh7F4MRV+6BeCToAP90ddvor5PWjpOVQUDO3yTxutxC1xlLg/Hczb7xMDi3ugOJ9mI2jr2MXrj26jeG5cQcwVdBhcoajP5wqZeYS9yiqPRSitnLQy9IrCMKP3oYgaOhl0S1XVg3FVBYUQZqb7CJpPwHp5XNxjVk+xzkP0bwNquMzqjYVtZ2ZYSIxNlnKzsQusaLRQ0Dv0Lb+vPfMKSI5H7TnMqUPE5vXtcl5gwYkQqALz3pRxGrvFl3eq92fL0AUzlY+hGuJjOqyQLlqpowlqzk+FWAAHRqHAPdrul8AAAAASUVORK5CYII=",
                symbol: function (val, params) {
                    return "circle"
                },
                itemStyle: {
                    normal: {
                        color: "#a6eb3a"
                    },
                    emphasis: {
                        areaColor: "#2B91B7"
                    }
                },
                data:[ { name: "拉萨贡嘎国际机场", value: [90.89, 29.29, "LXA"] }]
            }
        );
        
        var option = {
            tooltip: {
                trigger: "item",
                transitionDuration: 0,
            },
            legend: {
                textStyle: {
                    color: "#ffffff"
                }
            },
            geo: {
                map: "china",
                label: {
                    emphasis: {
                        show: true,
                        color: "#fff"
                    }
                },
                // 把中国地图放大了1.2倍
                zoom: 1.2,
                roam: true,
                itemStyle: {
                    normal: {
                        // 地图省份的背景颜色
                        areaColor: "#3a8dbf",
                        borderColor: "#6bbbd0",
                        borderWidth: 1
                    },
                    emphasis: {
                        areaColor: "#2B91B7"
                    }
                }
            },
            series: series
        };
        myEcharts.registerMap('china', china)
        this.chinaChart = myEcharts.init(
            document.getElementById("mapContain")
        );
        this.chinaChart.setOption(option);

```
这样即可得到一个中国地图