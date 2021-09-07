---
title: "지도 이동시키기"
sidebar_position: 2
---

지도를 이동시킵니다. 지도 객체의 메소드를 통해 지도를 원하는 좌표로 이동시킬 수 있습니다. 또, 지도가 표시되고 있는 영역크기를 벗어나지 않는 거리라면 애니메이션 효과처럼 지도를 부드럽게 이동시킬 수도 있습니다.

> original docs : https://apis.map.kakao.com/web/sample/moveMap/

```tsx live
function(){
  const MoveMapPosition = () => {
    // map 객체의 중심을 설정하는 함수를 가져오는 hook
    const setMapPosition = useMapPosition();

    return (
      <>
        <h5>ReactHook으로 이동시키기</h5>
        <div
          style={{
            display: "flex",
            gap: "10px",
          }}
        >
          <button onClick={() => setMapPosition({ lat: 33.452613, lng: 126.570888 })}>
            지도 중심좌표 이동시키기
          </button>
          <button onClick={() => setMapPosition({ lat: 33.45058, lng: 126.574942 }, true)}>
            지도 중심좌표 부드럽게 이동시키기
          </button>
        </div>
      </>
    );
  };

  const Main = () => {
     const [state, setState] = useState({
      // 지도의 초기 위치
      center: { lat: 33.452613, lng: 126.570888 },
      // 지도 위치 변경시 panto를 이용할지에 대해서 정의
      isPanto: false,
    })

    return (
      <>
        <Map // 지도를 표시할 Container
          center={state.center}
          isPanto={state.isPanto}
          style={{
            // 지도의 크기
            width: "100%",
            height: "450px",
            marginBottom: "10px",
          }}
          level={2} // 지도의 확대 레벨
        >
          <MoveMapPosition />
          <h5>State변경으로 이동시키기</h5>
          <div
            style={{
              display: "flex",
              gap: "10px",
            }}
          >
            <button
              onClick={() =>
                setState({
                  center: { lat: 33.452613, lng: 126.570888 },
                  isPanto: false,
                })
              }
            >
              지도 중심좌표 이동시키기
            </button>
            <button
              onClick={() =>
                setState({
                  center: { lat: 33.45058, lng: 126.574942 },
                  isPanto: true,
                })
              }
            >
              지도 중심좌표 부드럽게 이동시키기
            </button>
          </div>
        </Map>
      </>
    )
  }
  return (<Main/>)
}
```