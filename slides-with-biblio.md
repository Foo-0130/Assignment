---
title-slide: false
bibliography: references.bib
csl: vancouver.csl
citeproc: true
theme: serif
background-color: "#ffffff"
transition: slide
navigationMode: linear
hash: true
---

:::: {.columns}
::: {.column width="50%"}

## Sample slides
#### PlaceHolderName
#### Universiti Malaysia Perlis
#### [placeholder@email.com](mailto:placeholder@email.com)

<audio id="bg-music" src="media/audio/sb.m4a" loop></audio>

<div id="audio-credit"
     style="position: absolute; bottom: 40px; right: 20px; font-size: 0.6em; opacity: 0.6;">
  Music: “Adrift” by Scott Buckley (CC BY 4.0)
</div>

<script>
  document.addEventListener('DOMContentLoaded', () => {
    const audio = document.getElementById('bg-music');
    const credit = document.getElementById('audio-credit');

    // hide credit by default
    credit.style.display = 'none';

    const test = new Audio('media/audio/bgm.mp3');

    test.addEventListener('canplaythrough', () => {
      // bgm.mp3 exists → use it, keep credit hidden
      audio.src = 'media/audio/bgm.mp3';
    }, { once: true });

    test.addEventListener('error', () => {
      // bgm.mp3 missing → sb.m4a will play → show credit
      credit.style.display = 'block';
    }, { once: true });

    document.addEventListener('click', () => {
      if (Reveal.getIndices().h === 0) {
        audio.volume = 0.5;
        audio.play();
      }
    }, { once: true });

    Reveal.on('slidechanged', (event) => {
      if (event.indexh > 0) { audio.pause(); }
      else { audio.play(); }
    });
  });
</script>

:::

::: {.column width="50%"}
![](media/pics/logo1.png)
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Slide one
**Key Concepts:**
- Energy conservation per @carnot1824.
- $\Delta U = Q - W$
:::

::: {.column width="50%"}
![](media/pics/sample.png)
:::
::::

---

<span class="slide-title" data-title="My Hidden Slide Name"></span>

![](media/pics/wide.jpeg)

---

:::: {.columns}
::: {.column width="50%"}
### The Master Equation
The fundamental relation of thermodynamics:

$$\Delta U = Q - W$$

The work done $W$ is positive when the system expands against an external pressure.
:::

::: {.column width="50%"}
<video data-src="media/videos/sample.mp4" data-autoplay loop muted width="100%"></video>
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Visualizing the Gas Law
**Interactive Model:**

- P, V, and T relationships.
- Use the slider to adjust pressure.
- Observe the phase boundary.
:::

::: {.column width="50%"}
<iframe 
  data-src="media/plots/sample.html" 
  width="100%" 
  height="500px" 
  style="border:none;" 
  scrolling="no">
</iframe>
:::
::::

---

## Control Charts & Process Capability (Machine 1, Pressure 200kPa, Temp 338K)

:::: {.columns}
::: {.column width="50%"}
### PartLength Analysis

**Filtered Conditions:**
- Machine: 1
- Pressure: 200kPa
- Temperature: 338K

**Descriptive Statistics:**
- Mean: 49.9772
- Standard Deviation: 1.2387

**Process Capability (Assumed USL=52, LSL=48):**
- Cp: 0.5382
- Cpk: 0.5321

::: {.column width="50%"}
<iframe data-src='media/plots/partlength_xbar_chart_new.html' width='100%' height='250px' style='border:none;'></iframe>
<iframe data-src='media/plots/partlength_r_chart_new.html' width='100%' height='250px' style='border:none;'></iframe>
:::

---

### PartResistance Analysis

**Filtered Conditions:**
- Machine: 1
- Pressure: 200kPa
- Temperature: 338K

**Descriptive Statistics:**
- Mean: 5.9438
- Standard Deviation: 0.2478

**Process Capability (Assumed USL=7.5, LSL=6.5):**
- Cp: 0.6725
- Cpk: -0.7481

::: {.column width="50%"}
<iframe data-src='media/plots/partresistance_xbar_chart_new.html' width='100%' height='250px' style='border:none;'></iframe>
<iframe data-src='media/plots/partresistance_r_chart_new.html' width='100%' height='250px' style='border:none;'></iframe>
:::

::::
---

## Process Capability: Machine 2 (Pressure 200kPa, Temp 338K)

:::: {.columns}
::: {.column width="50%"}
### PartLength Analysis

**Filtered Conditions:**
- Machine: 2
- Pressure: 200kPa
- Temperature: 338K

**Descriptive Statistics:**
- Mean: 48.3725
- Standard Deviation: 0.5052

**Process Capability (Assumed USL=52, LSL=48):**
- Cp: 1.3197
- Cpk: 0.2458

::: {.column width="50%"}
<iframe data-src='media/plots/partlength_distribution_m2.html' width='100%' height='500px' style='border:none;'></iframe>
:::

---

### PartResistance Analysis

**Filtered Conditions:**
- Machine: 2
- Pressure: 200kPa
- Temperature: 338K

**Descriptive Statistics:**
- Mean: 4.1884
- Standard Deviation: 0.3942

**Process Capability (Assumed USL=7.5, LSL=6.5):**
- Cp: 0.4228
- Cpk: -1.9546

::: {.column width="50%"}
<iframe data-src='media/plots/partresistance_distribution_m2.html' width='100%' height='500px' style='border:none;'></iframe>
:::

::::
---

## Control Charts (Machine 1, Pressure 200kPa, Temp 338K)

:::: {.columns}
::: {.column width="50%"}
### PartLength Control Charts

**Filtered Conditions:**
- Machine: 1
- Pressure: 200kPa
- Temperature: 338K

The X-bar and R control charts for PartLength show the process mean and variability over time. Points within the control limits indicate a stable process, while points outside suggest special causes of variation.
:::

::: {.column width="50%"}
<iframe data-src='media/plots/partlength_xbar_chart_new.html' width='100%' height='250px' style='border:none;'></iframe>
<iframe data-src='media/plots/partlength_r_chart_new.html' width='100%' height='250px' style='border:none;'></iframe>
:::

---

### PartResistance Control Charts

**Filtered Conditions:**
- Machine: 1
- Pressure: 200kPa
- Temperature: 338K

Similarly, the X-bar and R control charts for PartResistance monitor its process mean and variability. These charts are crucial for identifying and addressing inconsistencies in the manufacturing process.
:::

::: {.column width="50%"}
<iframe data-src='media/plots/partresistance_xbar_chart_new.html' width='100%' height='250px' style='border:none;'></iframe>
<iframe data-src='media/plots/partresistance_r_chart_new.html' width='100%' height='250px' style='border:none;'></iframe>
:::

::::
---

## Process Capability: Machine 1 (Pressure 200kPa, Temp 338K)

:::: {.columns}
::: {.column width="50%"}
### PartLength Analysis

**Filtered Conditions:**
- Machine: 1
- Pressure: 200kPa
- Temperature: 338K

**Descriptive Statistics:**
- Mean: 49.9772
- Standard Deviation: 1.2387

**Process Capability (Assumed USL=52, LSL=48):**
- Cp: 0.5382
- Cpk: 0.5321

:::

::: {.column width="50%"}
<iframe data-src='media/plots/partlength_distribution_m2.html' width='100%' height='500px' style='border:none;'></iframe>
:::

---

### PartResistance Analysis

**Filtered Conditions:**
- Machine: 1
- Pressure: 200kPa
- Temperature: 338K

**Descriptive Statistics:**
- Mean: 5.9438
- Standard Deviation: 0.2478

**Process Capability (Assumed USL=7.5, LSL=6.5):**
- Cp: 0.6725
- Cpk: -0.7481

:::

::: {.column width="50%"}
<iframe data-src='media/plots/partresistance_distribution_m2.html' width='100%' height='500px' style='border:none;'></iframe>
:::

::::
---
# Bibliography
<div id="refs"></div>
