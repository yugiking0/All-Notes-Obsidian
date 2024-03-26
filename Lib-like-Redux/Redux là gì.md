# Redux là gì? 
Hiểu rõ cơ bản cách dùng Redux
---

## 1. Giới thiệu

Nói chung `Redux` khá là phổ biến. Tuy nhiên, không phải tất cả chúng ta đều biết nó là gì và cách sử dụng nó ra sao. Trong bài này, chúng ta sẽ xem vài lý do tại sao nên sử dụng `redux` bằng cách phân tích những lợi ích mà nó mang lại và cách hoạt động của nó.

## 2. Redux là gì?

**Redux** là một `predictable state management tool` cho các ứng dụng Javascript. Nó giúp bạn viết các ứng dụng hoạt động một cách nhất quán, chạy trong các môi trường khác nhau (client, server, and native) và dễ dàng để test. **Redux** ra đời lấy cảm hứng từ tư tưởng của ngôn ngữ **Elm** và kiến trúc **Flux** của Facebook. Do vậy Redux thường dùng kết hợp với React.

Do yêu cầu cho các ứng dụng `single-page` sử dụng Javascript ngày càng trở lên phức tạp thì code của chúng ta phải quản lý nhiều `state` hơn.

![[redux-store.png]]

> **`State`** có thể bao gồm là data trả về từ phía `Server` và được `cached` lại hay như dữ liệu được tạo ra và thao tác ở phía client mà chưa được đẩy lên phía server. `UI state` cũng trở lên phức tạp vì chúng ta cần quản lý việc `active Routes`, `selected tabs`, `spinners`, điều khiển phân trang …vv.


Với Redux, `state` của ứng dụng được giữ trong một nơi gọi là `store` và mỗi `component`đều có thể access bất kỳ state nào mà chúng muốn từ chúng store này.

## 3. Tại sao ta lại cần state management tool

Hầu hết các **lib** như `React`, `Angular`, etc được built theo một cách sao cho các `components` đến việc quản lý nội bộ các `state` của chúng mà không cần bất kỳ một thư viện or tool nào từ bên ngoài.

Nó sẽ hoạt động tốt với các ứng dụng có ít `components` nhưng khi ứng dụng trở lên lớn hơn thì việc quản lý states được chia sẻ qua các `components` sẽ biến thành các công việc lặt nhặt.

Trong một app nơi data được chia sẻ thông qua các `components`, rất dễ nhầm lẫn để chúng ta có thể thực sự biết nơi mà một state đang live. Một sự lý tưởng là data trong một `component` nên live trong chỉ một `component`. Vì vậy việc share data thông qua các `components` anh em sẽ trở nên khó khăn hơn.

Ví dụ, trong `react` để share data thông qua các `components` anh em, một state phải live trong component cha. Một method để update chính state này sẽ được cung cấp bởi chính `component` cha này và pass như props đến các `components` con.

Đây là một ví dụ:

```node
class App extends React.Component {
constructor(props) {
 super(props);
 this.state = { userStatus: "NOT LOGGED IN"}
 this.setStatus = this.setStatus.bind(this);
}

setStatus(username, password) {
 const newUsers = users;
 newUsers.map(user => {
   if (user.username == username && user.password === password) {
     this.setState({
       userStatus: "LOGGED IN"
     })
   }
 });
}

render() {
 return (
   <div>
     <Status status={this.state.userStatus} />
     <Login handleSubmit={this.setStatus} />
   </div>
 );
}
});
```

Giờ chúng ta hãy tưởng tượng rằng nếu một state phải được chia sẻ giữa các `component` cách khá xa nhau trong một `tree` `components` và state này phải được passed từ một `component` đến một `component` khác cho đến khi nó đến được nơi mà nó được gọi.

Cơ bản là, state mà chúng ta đang nói đến phải được nhấc lên một `component` cha gần nhất và tiếp nữa cho đến khi nó đến được cái component tổ tiên chứa tất cả các `components` nó cần cái state này sau đó pass cái state này xuống @@. Điều này sẽ khiến state trở nên khó hơn trong việc `maintain` và `less predictable`.

Điều này khiến cho bộ phận quản lý state trong app trở lên bừa bộn cũng như app trở lên vô cùng phức tạp. Đó là lý do tại sao chúng ta cần một `state management tool` như `Redux`.

## 4. Hiểu cách Redux làm việc

![[redux-tree-1.png]]

> Cái cách mà Redux hoạt động là khá đơn giản. Nó có 1 store lưu trữ toàn bộ state của app. Mỗi component có thể access trực tiếp đến state được lưu trữ thay vì phải send drop down props từ component này đến component khác.

Có 3 thành phần của Redux: `Actions`, `Store`, `Reducers`.

### _**1. Actions**_

`Actions` đơn giản là các events. Chúng là cách mà chúng ta send data từ app đến Redux store. Những data này có thể là từ sự tương tác của user vs app, API calls hoặc cũng có thể là từ form submission.

> `Actions` được gửi bằng cách sử dụng `store.dispatch()` method, chúng phải có một type property để biểu lộ loại action để thực hiện. Chúng cũng phải có một payload chứa thông tin. Actions được tạo thông qua một action creator. Ví dụ:

```node
   const setLoginStatus = (name, password) => {
       return {
         type: "LOGIN",
         payload: {
             username: "foo",
             password: "bar"
         }
       }
   }
```

### _**2. Reducers**_

`Reducers` là các function nguyên thủy chúng lấy state hiện tại của app, thực hiện một `action` và trả về một `state` mới. Những `states` này được lưu như những objects và chúng định rõ cách `state` của một ứng dụng thay đổi trong việc phản hồi một action được gửi đến `store`.

Đây là một ví dụ về cách mà `Reducers` hoạt động trong Redux:

```node
     const LoginComponent = (state = initialState, action) => {
         switch (action.type) {
           case "LOGIN":
               return state.map(user => {
                   if (user.username !== action.username) {
                       return user;
                   }
     
                   if (user.password == action.password) {
                       return {
                           ...user,
                           login_status: "LOGGED IN"
                       }
                   }
               });
               
           default:
               return state;
           } 
     };
```

### _**3. Store**_

`Store` lưu trạng thái ứng dụng và nó là duy nhất trong bất kỳ một ứng dụng `Redux` nào. Bạn có thể `access` các `state` được lưu, `update state`, và đăng ký or hủy đăng ký các `listeners` thông qua `helper methods`.

Tạo một `store` cho một `login app`:

```node
const store = createStore(LoginComponent);
```

Các `actions` thực hiện trên một state luôn luôn trả về một `state` mới. Vì vậy, `state` này là đơn giản và dễ đoán.

Bây giờ, chúng ta đã biết hơn một chúng về `Redux`, hãy trở lại với ví dụ `Login component` và xem cách cách mà `Redux` có thể giúp chúng ta được gì.

```node
    class App extends React.Component {
         render() {
             return (
                 <div>
                     <Status user={this.props.user.name}/>
                     <Login login={this.props.setLoginStatus}/>
                 </div>
             )
         }
     }
```

## **Nguyên lý vận hành**

![[redux-workflows.gif]]

# Cài đặt

```shell
npx create-react-app learn-reactjs
npm install --save react-router-dom
npm install @reduxjs/toolkit react-redux
cd learn-reactjs
npm start
```

## Tạo các thư mục

```md
learn-reactjs
├─ build
├─ node_modules
├─ public
└─ src
    ├─ api
    ├─ app
    │  └─ store.js
    ├─ components
    ├─ features 
    │  └─ Counter
    │     ├─ counterSlice.js
    │     └─ index.jsx
    ├─ App.css
    ├─ App.js
    └─ index.js    
```

# App
## Cung cấp Redux Store cho React

Chỉnh sửa file index.js

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import { BrowserRouter } from 'react-router-dom';
import App from './App';
import './index.css';
import reportWebVitals from './reportWebVitals';
import { Provider } from 'react-redux';
import store from './app/store';

ReactDOM.render(
  <React.StrictMode>
      <Provider store={store}>
          <BrowserRouter>
              <App />
          </BrowserRouter>
      </Provider>
  </React.StrictMode>,
  document.getElementById('root')
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```

Chỉnh sửa file app.js

```javascript
import { Redirect, Route, Switch } from 'react-router-dom';
import './App.css';
import CounterFeature from './features/Counter';

function App() {

  return (
    <div className="app">
      <Switch>
        <Redirect from="home" to="/" exact />
        <Route path="/products" component={CounterFeature} />
      </Switch>
    </div>
  );
}

export default App;
```

# Store

## Tạo một Redux Store

Tạo một Redux Store bằng cách chỉnh sửa file store.js trong thư mục store

```javascript
import couterReducer from '../features/Counter/counterSlice';
const { configureStore } = require("@reduxjs/toolkit");

const rootReducer = {
    counter: couterReducer,
}

const store = configureStore({
    reducer: rootReducer,
})

export default store
```

# Counter

## Tạo một slice state cho Redux

Tạo một slice state cho Redux bằng cách chỉnh sửa file counterSlice.js trong thư mục Counter. Tạo một slice yêu cầu một tên chuỗi để xác định slice, một giá trị trạng thái ban đầu và một hoặc nhiều hàm giảm thiểu để xác định cách state có thể được cập nhật. Khi slice được tạo, chúng ta có thể export các action Redux đã tạo và hàm giảm thiểu cho toàn bộ slice.

```javascript
import {createSlice} from '@reduxjs/toolkit';

const counterSlice = createSlice({
    name: 'counter', // tên chuỗi xác định slice
    initialState: 0, // giá trị khởi tạo ban đầu
    reducers: { // tạo các actions
        increase(state, action) { //action increase
            return state + 1;
        },
        decrease(state, action) { //action decrease
            return state - 1;
        },
    }
})

const { actions, reducer } = counterSlice
export const {increase, decrease} = actions // export action
export default reducer //ngầm hiểu chúng ta đang export counterSlice
```

## counter

Chỉnh sửa index.jsx trong thư mục Counter

```javascript
import React from 'react';
import { useDispatch, useSelector } from 'react-redux';
import { increase, decrease } from './counterSlice.js';

function CounterFeature(props) {
    //lấy counter ở rootReducer
    const counter = useSelector(state => state.counter) // useSelector là một hook giúp lấy 1 cái state trong root của mình
    const dispatch = useDispatch(); // sử dụng dispatch để gửi action

    const handleIncreaseClick = () => {
        const action = increase();
        dispatch(action);
    }

    const handleDecreaseClick = () => {
        const action = decrease();
        dispatch(action);
    }

    return (
        <div>
            <h1>Counter</h1>
            <p>Counter {counter}</p>
            <button onClick={() => handleIncreaseClick()} >increase</button>
            <button onClick={() => handleDecreaseClick()}>decrease</button>
        </div>
    );
}

export default CounterFeature;
```


Bài viết đến đây là kết thúc. Chúc các bạn thành công.


---