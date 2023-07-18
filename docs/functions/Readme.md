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

<tr>
<td> weightedRandomChoice() </td> <td> (choices: Array&lt;Dynamic&gt;, weights: Array&lt;Number&gt;) </td> <td> Returns a weighted random choice from an array based on supplied weights. </td>
<td style="width:550px">

<details>
<summary>Codeblock</summary>

```
function weightedRandomChoice(choices: Array<Dynamic>, weights: Array<Number>)
{
    //Error checking because I'm just responsible like that
    if (weights.length != choices.length){
        throw "Weights array is a different length than the choices array. Please ensure both argument arrays are the same length before calling the function.";
    }

    //Generate a random number between 0 and the sum of the weights
    var weightSum = 0;
    Engine.forEach(weights, function(weight, i) {
        //More error checking because I'm really really responsible I promise
        if(weight < 0) throw "weight " + weight + " at index " + i + " is negative. Please ensure all supplied weights are non-negative.";

        weightSum += weight; return true;
    }, []);
    var rNum = Random.getFloat(0, weightSum);

    //Run through the weights array until the sum of weights up to that point is less than or equal to the generated random number
    var choice = -1;
    weightSum = 0;
    Engine.forEach(weights, function(weight, index) {
        weightSum += weight;
        if(rNum <= weightSum) {
            choice = choices[index];
            return false;
        }
        return true;
    }, []);

    return choice;
}
```
</details>
</td>
</tr>


</table>
