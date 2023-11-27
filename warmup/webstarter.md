# web-starter 50

#### web exp time http://195.154.231.70:2345

clicking the button in the center of the site we get, ay, you're not a fridge!
![image](https://github.com/gamer-1478/unreal-ctf/assets/74775129/7c6693af-7b34-4339-aeb0-2b71a0768a62)


the comments of the site say 
``` <!-- TODO: only let in Samsung Smart Fridge 2.0 --> ```

there is also a script 

```

      document.getElementById("apiButton").addEventListener("click", () => {
        fetch("/ctfimg", { method: "POST" })
          .then((response) => response.text())
          .then((data) => {
            document.getElementById("responseText").innerText = data;
          })
          .catch((error) => console.error("Error:", error));
      });
```

posting the request with the modified user agent, 

![image](https://github.com/gamer-1478/unreal-ctf/assets/74775129/e48a4524-a20f-440c-a656-2142d6da2dbc)

we get the flag in base 64 ZFc1eVpXRnNlM1IzYVhSMFpYSmZabTl5WDNOaGJYTjFibWRmYzIxaGNuUmZabkpwWkdkbGZRPT0=

which upon decoding twice gives us the flag

``` flag - unreal{twitter_for_samsung_smart_fridge}```

