# Scandinavia 2026 — проект (continue-from-here)

Сайт-гид роуд-трипа **Berlin → Norway → Sweden → Berlin**. 12 дней · 4 человека ·
Range Rover Sport · ~5 000 км · природа, рыбалка, офроуд, без больших городов.

- **Live:** https://agdevua.github.io/scandinavia-2026/
- **Repo:** https://github.com/AGDevUA/scandinavia-2026 (GitHub user `AGDevUA`)

> Проект — **только сайт**. PDF больше не делаем.

---

## Маршрут (12 дней)

| День | Откуда → Куда | Главное |
|---|---|---|
| 1 | Berlin → Travemünde | Паром TT-Line (ночной) |
| 2 | Trelleborg → Omberg (оз. Vättern) | Шведский лес, парк Åsnen |
| 3 | Vättern → Dalarna (оз. Siljan) | Красные домики, рыбалка |
| 4 | Dalarna → Femundsmarka (NO) | Граница, грунтовки 4x4 |
| 5 | Femundsmarka (весь день) | Рыбалка, баня, белая ночь |
| 6 | Femundsmarka → Dovre | Røros (ЮНЕСКО), мускусные быки |
| 7 | Dovre → Geiranger | Trollstigen, паром фьорда |
| 8 | Stryn → Luster | Jostedalsbreen, горная грунтовка 4x4 |
| 9 | Luster → Aurland | Nærøyfjord (ЮНЕСКО, паром) |
| 10 | Aurland → Ulvik | Hardangerfjord, Vøringsfossen, рыбалка |
| 11 | Ulvik → Kristiansand | Setesdalen 4x4, паром домой |
| 12 | Hirtshals → Berlin | Финальный перегон |

## Паромы (рабочие URL)

1. Travemünde→Trelleborg · TT-Line · `ttline.com/en/sweden-ferries/travemuende-trelleborg/`
2. Geiranger→Hellesylt · Fjord1 · `fjord1.no/eng/routes-and-timetables/moere-og-romsdal/geiranger-hellesylt`
3. Gudvangen→Flåm · Lustrabaatane · `en.lustrabaatane.no/flam-gudvangen`
4. Kristiansand→Hirtshals · Color Line · `colorline.com/denmark-norway/ferry-hirtshals-kristiansand`

---

## Файлы (`/Users/ag2020/Downloads/AICode/Fun/`)

| Файл | Назначение |
|---|---|
| `index.html` | Весь сайт (HTML+CSS+JS в одном файле), контент на русском |
| `photos/day_00..12.jpg` | Обложка + фото-шапки 12 дней |
| `photos/ferry_01..04.jpg` | Фото 4 паромов (Wikimedia) |
| `photos/g_*.jpg` | Фото галерей дней (Wikimedia): `g_02_a g_03_a g_04_a g_06_a g_06_b g_07_a` |
| `.gitignore` | Исключает локальные служебные файлы из репо |

`Srart` — исходный бриф пользователя (локально, не в git).

## Структура сайта (секции в `index.html`)

`#top` Hero · `#overview` таблица маршрута + Google Maps · `#ferries` 4 карточки с фото ·
`#day-1…#day-12` (фото-шапка + текст + activities + блоки Паром/4WD + галерея + night-box) ·
`#tips` 6 карточек · `#booking` таблицы паромов/ночлегов/лицензий + бюджет + Google Maps.

## Дизайн и правила

- Палитра: `--forest #1B4332`, `--amber #B48C30`, `--cream #F5F1E9`.
- Шрифты: Playfair Display (заголовки) + Inter (текст), Google Fonts.
- Тон: товарищеский, спокойный, без слэнга/клише.
- **Топонимы — латиницей** (Geiranger, Vättern, Nærøyfjord…), обычные слова по-русски («озеро», «паром»).
- Фото — реальные с Wikimedia Commons (лицензия CC).

## Деплой

```bash
cd /Users/ag2020/Downloads/AICode/Fun
git add index.html main.md photos/
git -c user.email="ta.nu.da@gmail.com" -c user.name="ag2020" commit -m "..."
git push
```
Нужен **пользовательский `GH_TOKEN`** (`export GH_TOKEN=…` перед push) — в репо НЕ хранить.
CDN Fastly кэширует ~10 мин (`max-age=600`): сайт обновляется не мгновенно, для проверки
жёстко обновить браузер (Cmd+Shift+R) или `curl` с другим edge.

---

## Pending — следующий шаг (дёшево, без повторного поиска)

Докачать 8 фото галерей для дней 7–12 и вставить в `index.html`. URL уже найдены
(база: `https://upload.wikimedia.org/wikipedia/commons/`):

| Файл | День / слот | Путь после базы |
|---|---|---|
| `g_07_b` | 7 (добор → duo) | `1/16/Seven_Sisters_Waterfall_in_Geirangerfjord%2C_Norway.JPG` |
| `g_08_a` | 8 (single) | `2/2b/Briksdalsbreen%2C_the_arm_of_Jostedalsbreen_glacier_-_Norway_-_panoramio.jpg` |
| `g_09_a` | 9 (duo) | `d/d8/N%C3%A6r%C3%B8yfjord.JPG` |
| `g_09_b` | 9 (duo) | `9/97/Flam_station_-_Flam%2C_Norway_-_panoramio.jpg` |
| `g_10_a` | 10 (duo) | `b/b6/Voringsfossen_waterfall_at_Eidfjord%2C_Norway.jpg` |
| `g_10_b` | 10 (duo) | `7/79/Hovland_Hardangerfjorden_Norway.JPG` |
| `g_11_a` | 11 (single) | `8/8a/Aaraksboe_in_Setesdalen_1.JPG` |
| `g_12_a` | 12 (single) | `4/4b/Hirtshals-fyr-%C3%B8st.JPG` |

- Качать через `curl -A Mozilla/5.0` (Python ssl на этой машине ломается). Wikimedia
  отдаёт **429** при частых запросах — паузы 4–8с между файлами, проверять размер >10KB.
- Вставка перед `<div class="night-box …">` нужного дня:
  ```html
  <div class="gallery single fade-in">  <!-- или class="gallery duo …" для двух фото -->
    <figure class="gphoto"><img src="photos/g_XX.jpg" alt="…" loading="lazy"><figcaption>…</figcaption></figure>
  </div>
  ```
  CSS-классы `.gallery / .gallery.duo / .gphoto` уже есть в `index.html`.
- День 7 сейчас `gallery single` (только `g_07_a`) — при доборе `g_07_b` вернуть в `duo`.

## Сделано

Маршрут/паромы/офроуд · 13 фото-шапок · реальные фото паромов и части галерей ·
все внешние ссылки проверены и исправлены · топонимы латиницей · удалено «Питание: самостоятельно» ·
секция бронирования (паромы/ночлеги/лицензии/бюджет/Google Maps) · задеплоено на GitHub Pages.
