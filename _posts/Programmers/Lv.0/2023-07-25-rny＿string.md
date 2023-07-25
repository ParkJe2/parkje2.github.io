---
title: rny_string
categories: [Programmers, Lv.0]
tags: [Programmers]
---

> 문제를 직접 풀어보실 경우 [**여기**](https://school.programmers.co.kr/learn/courses/30/lessons/181863){:target="_blank"}를 클릭해 주세요.
{: .prompt-tip }

## 문제 설명

<p>'m'과 "rn"이 모양이 비슷하게 생긴 점을 활용해 문자열에 장난을 하려고 합니다. 문자열 <code>rny_string</code>이 주어질 때, <code>rny_string</code>의 모든 'm'을 "rn"으로 바꾼 문자열을 return 하는 solution 함수를 작성해 주세요.</p>

<hr>

### 제한사항

<ul>
<li>1 ≤ <code>rny_string</code>의 길이 ≤ 100</li>
<li><code>rny_string</code>은 영소문자로만 이루어져 있습니다.</li>
</ul>

<hr>

### 입출력 예
<div class="table-wrapper"><table>
        <thead><tr>
<th>rny_string</th>
<th>result</th>
</tr>
</thead>
        <tbody><tr>
<td>"masterpiece"</td>
<td>"rnasterpiece"</td>
</tr>
<tr>
<td>"programmers"</td>
<td>"prograrnrners"</td>
</tr>
<tr>
<td>"jerry"</td>
<td>"jerry"</td>
</tr>
<tr>
<td>"burn"</td>
<td>"burn"</td>
</tr>
</tbody>
      </table></div>
<hr>

### 입출력 예 설명

<p>입출력 예 #1</p>

<ul>
<li><p>예제 1번의 <code>rny_string</code>의 'm'을 "rn"으로 바꾸는 과정을 표로 나타내면 다음과 같습니다.</p>
<div class="table-wrapper"><table>
        <thead><tr>
<th>rny_string</th>
<th>m</th>
<th>a</th>
<th>s</th>
<th>t</th>
<th>e</th>
<th>r</th>
<th>p</th>
<th>i</th>
<th>e</th>
<th>c</th>
<th>e</th>
</tr>
</thead>
        <tbody><tr>
<td>result</td>
<td>rn</td>
<td>a</td>
<td>s</td>
<td>t</td>
<td>e</td>
<td>r</td>
<td>p</td>
<td>i</td>
<td>e</td>
<td>c</td>
<td>e</td>
</tr>
</tbody>
      </table></div>
<p>따라서 "rnasterpiece"를 return 합니다.</p></li>
</ul>

<p>입출력 예 #2</p>

<ul>
<li><p>예제 2번의 <code>rny_string</code>의 'm'을 "rn"으로 바꾸는 과정을 표로 나타내면 다음과 같습니다.</p>
<div class="table-wrapper"><table>
        <thead><tr>
<th>rny_string</th>
<th>p</th>
<th>r</th>
<th>o</th>
<th>g</th>
<th>r</th>
<th>a</th>
<th>m</th>
<th>m</th>
<th>e</th>
<th>r</th>
<th>s</th>
</tr>
</thead>
        <tbody><tr>
<td>result</td>
<td>p</td>
<td>r</td>
<td>o</td>
<td>g</td>
<td>r</td>
<td>a</td>
<td>rn</td>
<td>rn</td>
<td>e</td>
<td>r</td>
<td>s</td>
</tr>
</tbody>
      </table></div>
<p>따라서 "prograrnrners"를 return 합니다.</p></li>
</ul>

<p>입출력 예 #3</p>

<ul>
<li>예제 3번의 <code>rny_string</code>에는 'm'이 없습니다. 따라서 <code>rny_string</code> 그대로인 "jerry"를 return 합니다.</li>
</ul>

<p>입출력 예 #4</p>

<ul>
<li>예제 4번의 <code>rny_string</code>에는 'm'이 없습니다. 따라서 <code>rny_string</code> 그대로인 "burn"를 return 합니다.</li>
</ul>


## 문제 풀이

```js

function solution(rny_string) {
    const replace_rny_str = rny_string.replaceAll('m', 'rn')
    return replace_rny_str;
}

```

## 성능 요약

- 메모리: 33.4 MB

- 시간: 0.03 ms

