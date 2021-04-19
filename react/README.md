![ReactLifecycle](ReactLifecycle.png)

| Hook      | Lifecycle |
| ----------- | ----------- |
| useReducer -> useState | setState <br> default.state <br> this.state |
| useEffect | componentDidMount <br> componentDidUpdate <br> componentWillUnmount |
| useMemo | shouldComponentUpdate -> false |

createContext
- tạo Component chứa global state
- `useContext` để child component lấy state từ Context Component

`useRef`
- tạo ra 1 variable nằm ngoài lifecycle
- khi update không làm re-render
