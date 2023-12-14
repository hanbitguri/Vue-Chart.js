
# Vue-Chart.js

chart.js 간단사용법

### 설정

`Chart.register(...registerables)` <br/>

Chart.js에서 Chart.register() 함수를 사용하여 사용자 정의 차트 유형이나 플러그인을 등록하지 않으면,<br/>기본적으로 제공되는 Chart.js의 기본 차트 유형과 기능만 사용할 수 있습니다.

### 기본 템플릿

`const chart = new Chart(chartElement , chartOption)`

#### chartElement : ChartItem
```
type ChartItem =
  | string
  | CanvasRenderingContext2D
  | HTMLCanvasElement
  | { canvas: HTMLCanvasElement }
  | ArrayLike<CanvasRenderingContext2D | HTMLCanvasElement>
```
  
template의 canvas element 를 **dom selector** 혹은 **ref를 이용**해서 참조 해준다.

#### chartOption : ChartConfiguration

```
const chartOption = {
            type: chartType,
            data: {
                labels: 축에 나타낼 데이터 제목[],
                datasets: [
                    {
                        data: 축을 표현할 데이터[], //  => labels.length === data.length 
                        barThickness: 10, // 
                    },
                ],
            },
            //option?
            options: {
                // ---차트 전역 설정---
                color: "red", // legend 색상
                indexAxis: "y", // 축 방향 변경
                maintainAspectRatio: false, // 비율 고정 해제
                scales: {
                    x: {
                        grid: {
                            tickLength: 0, // 축과 시작점의 거리
                        },
                        ticks: {
                            padding: 4, // 축과 글자 사이 패딩
                        },
                    },
                },
                // ---차트 타입 별 설정---
                elements: {
                    bar: {
                        borderWidth: [1, 2, 3, 4],
                        hoverBorderColor: ["red", "blue", "yellow", "gray"],
                        backgroundColor: "#000",
                    },
                },
               // ---툴팁 , 범례 설정---
                plugins: {
                    // 호버 시 뜨는 툴팁 스타일 변경
                    tooltip: {
                        cornerRadius: 0,
                        xAlign: "center",
                    },
                    // legend 스타일 변경
                    legend: {
                        align: "start",
                        maxHeight: 102,
                    },
                },
            },
        }
```

- **chartType으로 올수있는 타입들**
  * bar
  * line
  * scatter
  * bubble
  * pie
  * doughnut
  * polarArea
  * radar

