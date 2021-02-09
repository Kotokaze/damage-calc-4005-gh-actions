# damage-calc
![](https://github.com/Kotokaze/damage-calc-4005-gh-actions/workflows/Damage%20Calculation%20Test/badge.svg)

このモジュールでは、ダメージ計算を行うことができます。  
ダメージ計算には

- 攻撃力
- 防御力
- 防御力貫通

以上 3 つの整数値が与えられ、結果としてダメージが整数値として得られます。

計算アルゴリズムは以下のように定義されます。

- 負の入力値があった場合には0として扱い、2000以上の入力値は2000として扱う。
- 実効防御力は、防御力 - 防御力貫通 で定義され、この実効防御力は、0未満にはならない。
- ダメージ減少率は、実効防御力 / (100 + 実効防御力) で定義され、
  ダメージは、攻撃力 * (1 - ダメージ減少率) を小数点以下で四捨五入した値となる。

## 使い方

```js
var dc = require('.');
console.log(dc.effectiveDamage(100, 50, 30));
```

以上を実行すると、

```
83
```

と表示されます。

以上の例では、攻撃力が 100、防御力が 50、防御力貫通が30で定義されています。  
実効防御力は、 50 - 30 で 20 となります。  
ダメージ減少率は、 20 / (100 + 20) であり、 1 / 6 です。
ダメージは、 100 * (1 - (1 / 6)) であり、 
計算すると 83.33333... となり、
小数点以下の四捨五入の結果、ダメージの 83 の値が得られます。
