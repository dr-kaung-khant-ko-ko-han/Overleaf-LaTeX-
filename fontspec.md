`\usepackage{fontspec}` သည် **XeLaTeX** နှင့် **LuaLaTeX** တို့တွင် စနစ်ဖောင့်များ (system fonts) ကို အလွယ်တကူ ရွေးချယ်သုံးစွဲနိုင်ရန် ဖန်တီးထားသည့် အဓိက package ဖြစ်ပါသည်။ မြန်မာစာ အပါအဝင် Unicode စာသားများ ရေးသားရာတွင် မရှိမဖြစ် အရေးပါပါသည်။

---

## ၁။ `fontspec` ဘာကြောင့်လိုအပ်သလဲ

- **Old system (pdfLaTeX)**: `fontenc` + `inputenc` package များဖြင့် အကန့်အသတ်ရှိသော Type 1 (PostScript) ဖောင့်များကိုသာ သုံးနိုင်ပြီး Unicode ကို ကောင်းစွာ မထောက်ပံ့ပါ။ မြန်မာစာ ရေးရန် အဆင်မပြေပါ။
- **Modern engine (XeTeX, LuaTeX)**: စက်ထဲထည့်ထားသော TrueType (.ttf) နှင့် OpenType (.otf) ဖောင့်များကို တိုက်ရိုက်သုံးနိုင်ပြီး Unicode ကို အပြည့်အဝ ထောက်ပံ့သည်။ `fontspec` က ထိုဖောင့်များကို LaTeX စာရွက်စာတမ်းအတွက် အလွယ်တကူ ချိတ်ဆက်ပေးသည်။

---

## ၂။ အခြေခံအသုံးပြုပုံ

### Package ခေါ်ယူခြင်း
```latex
\usepackage{fontspec}
```
ဤ command ကို preamble ( `\begin{document}` အထက်) တွင် ထည့်ရပါမည်။

### ပင်မဖောင့် သတ်မှတ်ခြင်း
```latex
\setmainfont{ဖောင့်အမည်}[Options]
\setsansfont{ဖောင့်အမည်}[Options] % sans-serif ဖောင့်
\setmonofont{ဖောင့်အမည်}[Options] % monospace ဖောင့်
```
- `\setmainfont` → စာကိုယ်တွင် ပုံမှန်သုံးမည့် ဖောင့်
- `\setsansfont` → `\textsf{}` သို့ `\sffamily` အတွက်
- `\setmonofont` → `\texttt{}` သို့ `\ttfamily` အတွက်

**ဥပမာ - Noto Sans Myanmar (Overleaf built-in)**
```latex
\usepackage{fontspec}
\setmainfont{Noto Sans Myanmar}[Script=Myanmar]
```

---

## ၃။ ဖောင့်ရွေးချယ်နည်း (၂) မျိုး

### (က) System font name ဖြင့်
စက်ထဲတွင် install လုပ်ထားသော ဖောင့်နာမည်ကို တိုက်ရိုက်ရေးပါ။
```latex
\setmainfont{Times New Roman}
```

### (ခ) ဖိုင်အမည်ဖြင့် (Overleaf တွင် upload လုပ်ထားလျှင်)
`Path`, `Extension`, `UprightFont` စသည့် options များဖြင့် တိကျစွာ ညွှန်းပါ။
```latex
\setmainfont{Pyidaungsu}[
    Path        = ./fonts/,      % ဖောင့်ဖိုင်ထားသည့် folder
    Extension   = .ttf,
    UprightFont = *-Regular,
    BoldFont    = *-Bold,
    Script      = Myanmar
]
```
- `Path` → ဖောင့်ဖိုင်ရှိရာ လမ်းကြောင်း ( `./` ဆိုလျှင် main file ရှိရာ folder)
- `Extension` → `.ttf` သို့ `.otf`
- `UprightFont`, `BoldFont`, `ItalicFont`, `BoldItalicFont` တို့တွင် `*` ကို ပင်မဖောင့်အမည်အဖြစ် အစားထိုးပေးသည်။ ဥပမာ `*` → `Pyidaungsu` ဖြစ်သွားပြီး နောက်မှ `-Regular` ဆက်သည်။

---

## ၄။ အရေးကြီး Options များ

`[ ... ]` အတွင်း comma ခြား၍ အောက်ပါတို့ကို ထည့်နိုင်သည်။

| Option | ရှင်းလင်းချက် | ဥပမာ |
|--------|----------------|-------|
| `Script` | OpenType script tag သတ်မှတ်ရန် (မြန်မာအတွက် `Myanmar`) | `Script=Myanmar` |
| `Language` | ဘာသာစကား tag (e.g., `English`, `Burmese`) | `Language=Burmese` |
| `Scale` | ဖောင့်အရွယ်ကို အချိုးကျ ချိန်ညှိရန် | `Scale=0.95` |
| `Ligatures` | စာလုံးဆက်များကို ဖွင့်/ပိတ်ရန် | `Ligatures=TeX` (default), `Ligatures=NoCommon` |
| `Numbers` | ဂဏန်းပုံစံ (OldStyle, Lining, Monospaced) | `Numbers=OldStyle` |
| `Color` | ဖောင့်အရောင် | `Color=red` |
| `BoldFont` | Bold ဖောင့်ဖိုင် သီးသန့်သတ်မှတ်ရန် | `BoldFont=MyFont-Bold.ttf` |
| `ItalicFont` | Italic ဖောင့်ဖိုင် | `ItalicFont=MyFont-Italic.ttf` |

**Script=Myanmar ဘာကြောင့်အရေးကြီးသလဲ**
OpenType ဖောင့်များတွင် စာလုံးပုံစံများ (glyphs) ကို ဘာသာစကားအလိုက် အထူးအစားထိုးပေးသည့် “script features” ရှိပါသည်။ `Script=Myanmar` သတ်မှတ်ပေးခြင်းဖြင့် မြန်မာစာလုံးပေါင်းပုံစံများ (ဥပမာ - ဆွဲကြိုး၊ ဝိုက်ချ၊ ထူးချ စသည့် context-dependent shaping) ကို မှန်ကန်စွာ ပြသနိုင်ရန် ဖောင့်အား ညွှန်ကြားပေးသည်။

---

## ၅။ OpenType Features များကို ထိန်းချုပ်ခြင်း

`fontspec` သည် OpenType layout features များကို အသေးစိတ် ထိန်းချုပ်နိုင်သည်။
```latex
\setmainfont{Padauk}[
    Script=Myanmar,
    RawFeature=+kdot;+mkmk  % manual feature activation
]
```
သို့သော် ယေဘုယျအားဖြင့် `Script=Myanmar` ထည့်ထားရုံဖြင့် လိုအပ်သည့် features များ အလိုအလျောက် ဖွင့်ပေးပါသည်။

---

## ၆။ မြန်မာစာအတွက် စာကြောင်းခွဲခြင်း (Line Breaking)

`fontspec` နှင့် တွဲဖက်၍ XeTeX ၏ စာကြောင်းခွဲစနစ်ကို မြန်မာလို သတ်မှတ်ပေးရန် အောက်ပါ command များ ထည့်ပါ။
```latex
\XeTeXlinebreaklocale "my"
\XeTeXlinebreakskip = 0pt plus 1pt
```
ဤသို့မလုပ်ပါက စာကြောင်းအဆုံးတွင် စာလုံးများ ကျော်ထွက်ခြင်း၊ ဆွဲကြိုးများ ပြတ်တောက်ခြင်း ဖြစ်တတ်ပါသည်။

---

## ၇။ pdfLaTeX နှင့် ကွာခြားချက်

| | pdfLaTeX | XeLaTeX/LuaLaTeX + fontspec |
|----------|----------|----------------------------|
| Font engine | Type 1 (Metafont) | System TTF/OTF |
| Unicode | မပြည့်ဝ | အပြည့်အဝ |
| မြန်မာစာ | ရှုပ်ထွေး/မဖြစ်နိုင်သလောက် | လွယ်ကူစွာ ရေးနိုင် |
| Font ရွေးချယ်မှု | `fontenc`, `inputenc` | `fontspec` |

---

## ၈။ နမူနာ အပြည့်အစုံ (Pyidaungsu + English)

```latex
% !TEX program = XeLaTeX
\documentclass{article}
\usepackage{fontspec}

\setmainfont{Pyidaungsu}[
    Path        = ./,
    Extension   = .ttf,
    UprightFont = *-Regular,
    BoldFont    = *-Bold,
    Script      = Myanmar
]

% English sans-serif အတွက်သီးသန့်
\setsansfont{Noto Sans}[Script=Latin]

\XeTeXlinebreaklocale "my"
\XeTeXlinebreakskip = 0pt plus 1pt

\begin{document}
\section*{မြန်မာဘာသာ စာစီစာရိုက်}
Pyidaungsu ဖောင့်ဖြင့် ရေးသားထားသော စာပိုဒ်ဖြစ်ပါသည်။\\
\textbf{ထူထဲသောစာလုံး} နှင့် \textsf{English sans-serif} ရောရေးနိုင်သည်။
\end{document}
```

---

## ၉။ အဖြစ်များသော ပြဿနာများ

1. **ဖောင့်မတွေ့ပါက**  
   - ဖိုင်နာမည် စာလုံးပေါင်း မှန်မမှန် စစ်ပါ။  
   - Overleaf တွင် ဖိုင်ကို main file နှင့် တစ်ဖိုလ်ဒါတည်းထားပါ။  
   - System font name တွင်လည်း အမည်အတိအကျ မှန်ကန်ရန် လိုပါသည် (Windows font viewer မှ ကူးယူနိုင်သည်)။

2. **စာလုံးပေါင်းပုံစံ မမှန်လျှင်**  
   - `Script=Myanmar` မေ့နေတတ်သည်။ ထည့်ပေးပါ။  
   - တစ်ခါတစ်ရံ `RawFeature=+mkmk` ထည့်ရန် လိုအပ်သော ဖောင့်များရှိတတ်သည်။

3. **Overleaf compile နှေးလျှင်**  
   - LuaLaTeX က XeLaTeX ထက် ပိုနှေးတတ်၍ XeLaTeX ကို ရွေးပါ။  
   - ဖောင့်ဖိုင်များ ကြီးမားပါက (ဥပမာ Noto Sans Myanmar) တစ်ခါတစ်ရံ cache ပြုလုပ်ရန် အချိန်ယူတတ်သည်။

---

`fontspec` သည် ခေတ်မီ LaTeX အသုံးပြုသူတိုင်း မြန်မာစာမက မည်သည့် Unicode စာကိုမဆို လှပစွာ ရေးသားနိုင်ရန် အခြေခံကျသော package ဖြစ်ပါသည်။ XeTeX/LuaTeX ဖြင့် စာစီစာရိုက်ရာတွင် ဤ package မပါဘဲ မဖြစ်နိုင်သလောက်ပင် ဖြစ်ပါသည်။
