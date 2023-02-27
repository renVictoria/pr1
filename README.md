# neural-style

Это имплементарная реализация статьи [«Нейронный алгоритм художественного стиля» ](http://arxiv.org/abs/1508.06576)
 Леона А. Гатиса, Александра С. Эккера и Матиаса Бетге.

В работе представлен алгоритм объединения содержимого одного изображения со стилем другого изображения с использованием сверточных нейронных сетей. Вот пример, который отображает художественный стиль 
[«Звездной ночи» ](https://en.wikipedia.org/wiki/The_Starry_Night)
на ночной фотографии кампуса Стэнфорда:

<div align="center">
 <img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/starry_night_google.jpg" height="223px">
 <img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/hoovertowernight.jpg" height="223px">
 <img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/starry_stanford_bigger.png" width="710px">
</div>

Применение стиля разных изображений к одному и тому же изображению контента дает интересные результаты.
Здесь мы воспроизводим рисунок 2 из статьи, на котором изображена фотография Тюбингена в Германии в разнообразие стилей:

<div align="center">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/tubingen.jpg" height="250px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/tubingen_shipwreck.png" height="250px">

<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/tubingen_starry.png" height="250px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/tubingen_scream.png" height="250px">

<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/tubingen_seated_nude.png" height="250px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/tubingen_composition_vii.png" height="250px">
</div>

Вот результаты применения стиля различных произведений искусства к этой фотографии
Мост "Золотые ворота:


<div align="center"
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/golden_gate.jpg" height="200px">

<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/frida_kahlo.jpg" height="160px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_kahlo.png" height="160px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/escher_sphere.jpg" height="160px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_escher.png" height="160px">
</div>

<div align="center">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/woman-with-hat-matisse.jpg" height="160px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_matisse.png" height="160px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/the_scream.jpg" height="160px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_scream.png" height="160px">
</div>

<div align="center">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/starry_night_crop.png" height="160px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_starry.png" height="160px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/seated-nude.jpg" height="160px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_seated.png" height="160px">
</div>

### Content / Style Tradeoff

Алгоритм позволяет пользователю найти компромисс между относительным весом условий реконструкции стиля и содержания,
как показано в этом примере, где мы переносим стиль [Пикассо 1907 года](http://www.wikiart.org/en/pablo-picasso/self-portrait-1907) onto Brad Pitt:

<div align="center">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/picasso_selfport1907.jpg" height="220px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/inputs/brad_pitt.jpg" height="220px">
</div>

<div align="center">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/pitt_picasso_content_5_style_10.png" height="220px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/pitt_picasso_content_1_style_10.png" height="220px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/pitt_picasso_content_01_style_10.png" height="220px">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/pitt_picasso_content_0025_style_10.png" height="220px">
</div>

### Style Scale

Изменяя размер изображения стиля перед извлечением признаков стиля, мы можем контролировать типы художественных изображений.
черты, перенесенные из стиля изображения; вы можете управлять этим поведением с помощью флага `-style_scale`.
Ниже мы видим три примера рендеринга моста Золотые Ворота в стиле «Звездная ночь».
Слева направо, `-style_scale` is 2.0, 1.0, and 0.5.

<div align="center">
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_starry_scale2.png" height=175px>
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_starry_scale1.png" height=175px>
<img src="https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_starry_scale05.png" height=175px>
</div>
