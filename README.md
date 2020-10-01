## 轉寫方案

使用 `0` 輸入清化符號 ` ̥`。

```python
from itertools import product
import re


senmu=["p", "ph", "b", "f", "v", "m", "'m", "ts", "tsh", "s", "z", "zh", "c", "ch", "j", "sh", "l", "'l", "t", "th", "d", "n", "'n", "k", "kh", "g", "ng", "'ng", "", "h", "gh"]

yuinmu=['a', 'ua', 'ia', 'o', 'io', 'y', 'i', 'u', 'iu', 'e', 'ue', 'au', 'iau', 'eu', 'ieu', 'ae', 'uae', 'iae', 'ie', 'oe', 'uoe', 'ioe', 'an', 'uan', 'ian', 'aon', 'uaon', 'iaon', 'on', 'ion', 'en', 'uen', 'in', 'iuin', 'aeh', 'uaeh', 'iaeh', 'eh', 'ueh', 'ih', 'iuih', 'oh', 'ioh', 'ah', 'uah', 'iah']

ipasenmu=["p", "pʰ", "b", "f", "v", "m", "ʔm", "t͡s", "t͡sʰ", "s", "z", "ʑ", "t͡ɕ", "t͡ɕʰ", "d͡ʑ", "ɕ", "l", "ʔl", "t", "tʰ", "d", "n", "ʔn", "k", "kʰ", "g", "ŋ", "ʔŋ", "ʔ", "h", "ɦ"]

ipayuinmu=["a", "ʷa", "ia", "o", "yo", "z̩", "iᶽ", "ɤᵝ", "yᶽ", "e", "ʷe", "ɒ", "iɒ", "ɤɯ", "iɤɯ", "ɛ", "ʷɛ", "iɛ", "iɪ", "ø", "ʷø", "yø", "ã", "ʷã", "iã", "ɒ̃", "ʷɒ̃", "iɒ̃", "ɔŋ", "iɔŋ", "əŋ", "ʷəŋ", "ɪɲ", "yʏɲ", "ɐʔ", "ʷɐʔ", "iɐʔ", "əʔ", "ʷəʔ", "ɪʔ", "yʏɪʔ", "ɔʔ", "iɔʔ", "ɒʔ", "ʷɒʔ", "iɒʔ"]

sytsheh=[pi[0]+'\t'+pi[1] for pi in zip([pi[0]+pi[1] for pi in product(ipasenmu,ipayuinmu)],[pi[0]+pi[1] for pi in product(senmu,yuinmu)])]


sytsheh=[re.sub(r"\t'([aeiouy])",r"\1",i) for i in sytsheh]

sytsheh=[re.sub(r"([ʔɦ])ʷ",r"\1u",i) for i in sytsheh]

sytsheh=[i for i in sytsheh if not re.search(r'\t[c|j][aeouy]', i)]
sytsheh=[i for i in sytsheh if not re.search(r'\t[c|s|z]h[aeouy]', i)]

sytsheh=[re.sub(r"(f)ɤᵝ",r"\1v̩",i) for i in sytsheh]
sytsheh=[re.sub(r"vɤᵝ",r"v̩ᵝ",i) for i in sytsheh]
sytsheh=[re.sub(r"([pbm])ɤᵝ",r"\1ɯᵝ",i) for i in sytsheh]
sytsheh=[re.sub(r"(pʰ)ɤᵝ",r"\1ɯᵝ",i) for i in sytsheh]
```