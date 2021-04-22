<script>
  import { onMount } from "svelte";

  export let g;
  let num = 0;

  onMount(() => {
    reg();
  });
  function fatoen(e) {
    let y = e;

    let a = ["۰", "۱", "۲", "۳", "۴", "۵", "۶", "۷", "۸", "۹"];
    for (let i = 0; i < e.length; i++) {
      for (let j = 0; j < 10; j++) {
        if (e[i] == a[j]) {
          y[i] = j;
        }
      }
    }
    return y;
  }
  function entofl(strin) {
    let reach = false;
    let bool = false;
    let s = 0;
    for (let i = 0; i < strin.length; i++) {
      if (bool) {
        break;
      }
      if (reach) {
        bool = true;
      }

      if (strin[i] == "٫") {
        reach = true;
      } else {
        s = s + strin[i];
        s = s * 10;
      }
    }

    s = reach ? s / 100 : s / 10;
    console.log(s);
    return s;
  }
  function reg() {
    if (typeof g === "string" && g !== null) {
      let rg = /([٫۰۱۲۳۴۵۶۷۸۹]*) مگابایت|([٫۰۱۲۳۴۵۶۷۸۹]*) گیگابایت/giu;
      let x = rg.exec(g);

      console.log(x);
      let tip = x[1] ? "۱" : x[2] ? x[2] : "I Dont Know";

      console.log("tip=" + tip);
      console.log(typeof tip);
      let f = tip.split("");
      console.log(f);
      let z = fatoen(f);
      let fl = entofl(z);
      console.log(fl);
      return (num = fl ? Math.ceil(fl) : 0);
    } else {
      console.log(g);
    }
  }
</script>

<div class="text">
  قیمت خرید بر روی دیسک
  <span class=" text-danger">
    {Math.ceil(num / 4) * 8000}
    تومان
  </span>
</div>
