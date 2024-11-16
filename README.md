# Astro
## Project Structure
### 目錄
- src/ 專案原始碼
- public/ 未經astro處理的資源，icon、字體、圖片等
- package.json 專案列表
- astro.config.mjs astro設定檔
- tsconfig.js typescript設定檔

## Rendering Modes
### Pre-rendered
- 預設的模式為靜態outpur:'static'，也就是在build的時候將所有頁面轉換成HTML。
- 靜態網站生成（static site generation,SSG）
### On-demand rendered
- output: 'server' 適合高動態網站
- output: 'hybrid' 適合靜態為主的
- server-side rendering,SSR
- 適合頻繁更新、有資料庫、授權等功能的網站
## 模板語法
### 變數
```astro
---
const title = 'astro';
---
<h1>{title}</h1>
```
### 動態屬性
```html
---
const sty = 'active'
---
<div class={sty}>測試</div>
```
> 雖然可以指定屬性給html，但要注意無法指派事件（如按鈕事件）給html。
```astro
---
function handleClick () {
    console.log("button clicked!");
}
---
<!-- ❌ 無法這麼做！❌ -->
<button onClick={handleClick}>點選這個按鈕，什麼事也不會發生！</button>
```
### 動態HTML
```astro
<ul>
    {
        drinks.map(drink => <li>{drink}</li>)
    }
</ul>

<div>
    {isAdmin ? 'Admin' : 'Guest'}
</div>
<div>
    {isAdmin && '管理員'}
</div>
```
<!-- ### Fragment -->
<!-- ### 動態標籤 -->
### Astro 與 JSX
#### 屬性
```astro
<!-- JSX -->
<div className="box" dataValue="3" />
<!-- ASTRO -->
<div class="box" data-value="3" />
```
#### 複數元素
```astro
<p>不需要用容器把多個元素包起來。</p>
<p>Astro 模板支援複數根元素。</p>
```
#### 註解
```astro
<!-- HTML 註解語法在 .astro 檔案是合法的 -->
{/* JS 註解語法也同樣合法 */}
```
