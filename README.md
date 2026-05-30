# Overleaf-LaTeX

Pyidaungsu ဖောင့် သုံးမယ်ဆိုရင် Overleaf ထဲကို ဖောင့်ဖိုင် တင်ပြီး XeLaTeX/LuaLaTeX နဲ့ compile လုပ်ရပါမယ်။

---

### ၁။ Pyidaungsu ဖောင့်ဖိုင်ရယူပါ
Pyidaungsu ဖောင့်ကို ကွန်ပျူတာထဲတွင် ရှိပြီးသားဆိုရင် `.ttf` (သို့) `.otf` ဖိုင်ကို Overleaf project ထဲ တင်ပါ။  
မရှိသေးရင် **Pyidaungsu** ဖောင့်ကို အွန်လိုင်းမှ ဒေါင်းလုဒ်လုပ်ပြီး `Pyidaungsu-Regular.ttf` စသဖြင့် သိမ်းထားပါ။

---

### ၂။ Overleaf ထဲ ဖောင့်ဖိုင်တင်ပါ
1. Overleaf project ထဲဝင်ပါ။  
2. ဘယ်ဘက်ရှိ **ဖိုင်တွဲ (folder) icon** ကိုနှိပ်ပြီး **Upload** မှ ဖောင့်ဖိုင်ကို တင်ပါ။  
   (ဖိုင်နာမည်ကို English လိုပဲထားပါ၊ ဥပမာ - `Pyidaungsu-Regular.ttf`)

---

### ၃။ Compiler ကို XeLaTeX ရွေးပါ
**Menu** → **Compiler** → `XeLaTeX` (သို့) `LuaLaTeX` ရွေးပေးပါ။

---

### ၄။ LaTeX ကုဒ်တွင် သတ်မှတ်ပါ
အောက်ပါ နမူနာကုဒ်ကို သုံးပါ။ (ဖိုင်နာမည်နဲ့ extension ကိုယ့်ဖိုင်နဲ့ ကိုက်ညီအောင် ပြင်ပါ။)

```latex
% !TEX program = XeLaTeX
\documentclass{article}
\usepackage{fontspec}

% Pyidaungsu ဖောင့်သတ်မှတ်ခြင်း
% ဖိုင်နာမည် "Pyidaungsu-Regular.ttf" ဆိုပါစို့
\setmainfont{Pyidaungsu}[
    Path        = ./,
    Extension   = .ttf,
    UprightFont = *-Regular,
    Script      = Myanmar
]

% စာကြောင်းခွဲခြင်း (Line breaking) ကောင်းမွန်စေရန်
\XeTeXlinebreaklocale "my"
\XeTeXlinebreakskip = 0pt plus 1pt

\begin{document}
မင်္ဂလာပါ။ ဤစာသားသည် Pyidaungsu ဖောင့်ဖြင့် ရိုက်ထားသည်။

အင်္ဂလိပ်စာ English text ပါရေးလို့ရသည်။
\end{document}
```

**ရှင်းလင်းချက်**
- `Path = ./` → ဖောင့်ဖိုင်ကို project root မှာထားလျှင် ဒီအတိုင်းထားပါ။  
- `Extension = .ttf` → ဖိုင်ရဲ့ extension က `.ttf` ဆိုရင်။ `.otf` ဆိုရင် `.otf` လို့ပြောင်းပါ။  
- `UprightFont = *-Regular` → ဖိုင်နာမည်တွင် `Pyidaungsu-Regular` ဆိုရင် `*` သည် `Pyidaungsu` ဖြစ်ပြီး နောက်မှာ `-Regular` ပေါင်းထည့်ပေးပါတယ်။ ဖိုင်နာမည် `Pyidaungsu.ttf` တစ်ခုတည်းဆိုရင် `UprightFont` မထည့်ဘဲ `\setmainfont{Pyidaungsu}[Path=./, Extension=.ttf, Script=Myanmar]` လို့ ရေးနိုင်ပါတယ်။  
- `Script=Myanmar` ကို မမေ့ပါနဲ့။

---

### ၅။ Bold/Italic ဖောင့်များပါ တင်ချင်ရင်
Pyidaungsu မှာ Bold ဖိုင်ရှိရင် (ဥပမာ `Pyidaungsu-Bold.ttf`)၊ အောက်ပါအတိုင်း ထည့်နိုင်ပါတယ်။

```latex
\setmainfont{Pyidaungsu}[
    Path        = ./,
    Extension   = .ttf,
    UprightFont = *-Regular,
    BoldFont    = *-Bold,
    Script      = Myanmar
]
```

---

အခုဆိုရင် Overleaf ပေါ်မှာ Pyidaungsu ဖောင့်နဲ့ မြန်မာစာ လှလှပပပေါ်လာပါလိမ့်မယ်။ စမ်းကြည့်ပြီး အဆင်မပြေတာရှိရင် ထပ်မေးနိုင်ပါတယ်။
