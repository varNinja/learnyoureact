먼저 `Hello World`를 출력해 봅시다!

제일 먼저, 모듈을 설치합시다.
밑의 명령을 실행해 보세요.

`$ npm install express`

`$ npm install body-parser`

`$ npm install express-react-views`

`$ npm install node-jsx`

그런 다음, `program.js`를 만들어 다음과 같은 내용을 적습니다.

```
var express = require('express');
var app = express();

app.set('port', (process.argv[2] || 3000));
app.set('view engine', 'jsx');
app.set('views', __dirname + '/views');
app.engine('jsx', require('express-react-views').createEngine());

require('node-jsx').install();

app.use('/', function(req, res) {
  res.render('index', '');
});

app.listen(app.get('port'), function() {});
```
위의 코드가 렌더링을 하는 서버 쪽의 코드입니다. `express-react-views`라는 모듈을 사용해, `/`에 들어올 때 `views/index.jsx`을 읽어오도록 되어 있습니다.


다음으로 `program.js`이 있는 디렉터리에서 `views` 디렉터리를 만들어, 그 안에서 `index.jsx`를 만들어 주세요.
`index.jsx`에는 다음과 같은 내용이 들어갑니다.

```
var React = require('react');

var TodoBox = React.createClass({
  render: function() {
    return (
      <div className="todoBox">
        Hello, world!
      </div>
    );
  }
});

module.exports = TodoBox;
```

위의 JavaScript 안에 XML을 작성하는 듯한 코드가 React의 JSX라 불리는 방법입니다.
다르게 적는 방법도 있지만, 이 워크숍에서는 전부 JSX로 작성하도록 하겠습니다.

React.js 문서는 여기서 찾으실 수 있습니다. https://facebook.github.io/react/docs/getting-started-ko-KR.html

JSX 문법에 관한 더 자세한 내용은 여기서 읽으실 수 있습니다. https://facebook.github.io/react/docs/jsx-in-depth-ko-KR.html

준비가 되면, `node program.js`를 실행해 `http://localhost:3000`으로 들어가, 실제로 HTML이 출력되는 것을 확인하세요.
그런 다음, `learnyoureact verify program.js`를 실행하세요.
