# [Nomade Code][0]
## Movie App 2019

React JS Fundamentals Course (2019 Update)
> Lesson : [ReactJS로 웹 서비스 만들기 - (중급) JavaScript, ReactJS][1]
> Libraries : react, [axios][axios], [gh-pages][gh-pages], [react-router-dom][react-router-dom]


#### 2020.01.29 
1. Component 는 HTML을 반환하는 함수이다. 
2. JSX 는 Javascript 와 HTML 을 결합한 형식이다.
3. JSX 는 Component 에 정보를 보낼 수 있다. 
4. React Application 은 한번에 하나의 Component 만 Rendering 할 수 있다. 
   ```
   # index.js
   ReactDOM.render(<App />, document.getElementById('root'));
   ```


#### 2020.01.30
1. react 기본 구성은 다음과 같다. 
   ```
   # App.js
   class App extends React.Component {...}
   ```
2. render() 은 화면을 그릴 때 사용한다. 
3. State 는 동적인 데이터를 다룰 때 사용한다. 
4. setState 를 호출할 때 마다 react 는 새로운 state 와 함께 redner function 을 호출한다. 
5. react method 는 Life Cycle 를 갖는다. (호출순서가 있다.)
   > Reference : [Life Cycle Method][2]
   1. Mounting : component 가 생성되어 DOM 에 추가될 때 호출된다.
      1. **constructor()**
      2. static getDerivedStateFromProps()
      3. **render()**
      4. **componentDidMount()**
   2. Updating : Props or State 가 변경되면 호출된다. 
      1. static getDerivedStateFromProps()
      2. shouldComponentUpdate()
      3. **render()**
      4. getSnapshotBeforeUpdate()
      5. **componentDidUpdate()**
   3. Unmounting : component 가 DOM에서 제거될 때 호출된다. 
      1. **componentWillUnmount()**


#### 2020.02.11
1. Fetch() 를 사용할 수 있지만 Fetch Wrapper 인 axios 를 사용한다. 
2. 비동기 처리가 필요할 경우 async, await 를 사용한다. 
   ```
   getMovies = async () => {
    const movies = await axios.get("https://yts-proxy.now.shlist_movies.json");
   }
   ```
3. 필요한 결과가 movies.data.data.movies 에 저장된 경우 다음과 같이 저장할 수 있다.
   ```
   # ~ ES5 
   getMovies = async () => {
    const movies = await axios.get("https://yts-proxy.now.sh/list_movies.json?sort_by=rating"); 
    this.setState({movies.data.data.movies, isLoading: false});
   };

   # ES6 ~  
   getMovies = async () => {
    const {data : {data : {movies}}} = await axios.get("https://yts-proxy.now.sh/list_movies.json?sort_by=rating");
    this.setState({movies, isLoading: false});
   };
   ```



[0]:https://academy.nomadcoders.co/courses/category/KR
[1]:https://academy.nomadcoders.co/p/reactjs-fundamentals
[2]:https://ko.reactjs.org/docs/react-component.html#mounting
[axios]:https://www.npmjs.com/package/axios
[gh-pages]:https://www.npmjs.com/package/gh-pages
[react-router-dom]:https://www.npmjs.com/package/react-router-dom