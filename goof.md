# GOOF - 200

#### math time nc 195.154.231.70 2000


Inspiration - https://nikos-titomichelakis.medium.com/uniwa-2021-ctf-fast-calculator-writeup-ea2cfb96af3 

(a much better writeup than mine)

my solution was

```js
const NetcatClient = require('netcat/client')
var stringMath = require('string-math');
const nc = new NetcatClient()

nc.enc('utf8').addr('195.154.231.70').port(2000).connect().on('data', function (data) {
    if (!data.includes("unreal")) {
        let calc = data.split(/\r?\n/);
        console.log(calc);
        calc = calc[1]
        calc = calc.replace(' = ?', '');
        console.log(calc);
        calc = stringMath(calc);
        console.log(calc);
        nc.send(calc.toString() + '\n');
    }
    else {
        console.log(data);
    }

})
```

which gives the flag

```
flag - unreal{i_hope_you_didn't_try_manually..}
```
