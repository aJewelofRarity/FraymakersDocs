---
layout: default
title: Custom Functions
description: Several custom made functions to help in fraytools
---

<table>
<tr>
<th> Function </th> <th> Arguments </th> <th> Description </th> <th> Code </th>
</tr>

<tr>
<td> setAngleSpeed() </td> <td> (angle:Float, speed:Float) </td> <td> Applys a set speed in a set direction instead of using X and Y </td>
<td style="width:550px">

<details>
<summary>Codeblock</summary>

```
function setAngleSpeed(angle:Float, speed:Float) {
  var rads:Float = -angle * (Math.PI / 180);
  var m_X:Float = Math.cos(rads);
  var m_Y:Float = Math.sin(rads);
  self.setXSpeed(m_X * speed);
  self.setYSpeed(m_Y * speed);
}
```
</details>
</td>
</tr>
</table>
