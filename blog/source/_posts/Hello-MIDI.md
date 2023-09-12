---
title: Hello MIDI
date: 2023-09-11
tags:
---

Welcome to our first blogpost about MIDI!

![wtf](assets/Hello-MIDI/pianoroll-a.png)

A different way to display the image:

Just to left:

<img src="/assets/Hello-MIDI/pianoroll-a.png" alt="pianoroll" style="height: 220px; display: block; float: left;">
<div style="clear: both;"></div>


Just to right:

<img src="/assets/Hello-MIDI/pianoroll-a.png" alt="pianoroll" style="height: 220px; display: block; float: right;">
<div style="clear: both;"></div>


Just in center:

<img src="/assets/Hello-MIDI/pianoroll-a.png" alt="Image Alt Text" style="height: 220px; display: block; margin: 0 auto;">
<div style="clear: both;"></div>

Just to left again:

<img src="/assets/Hello-MIDI/pianoroll-a.png" alt="pianoroll" style="height: 220px; display: block; float: left;">
<div style="clear: both;"></div>

Part of the code used to generate this:

```python
from typing import Callable
                           
import numpy as np         
import pandas as pd        


class TimeGrid:                                                      
    def __init__(                                                    
        self,                                                        
        nonlinearity: Callable,                                      
        n_measures: int = 4,                                         
        ticks_per_measure: int = 16,                                 
        measure_duration_s: float = 1,                               
    ):                                                               
        self.n_measures = n_measures                                 
        self.ticks_per_measure = ticks_per_measure                   
                                                                     
        # One measure is a sine period -> 2.pi                       
        stop = n_measures * 2 * np.pi                                
        steps = n_measures * ticks_per_measure                       
        self.linear_grid = np.linspace(                              
            start=0,                                                 
            stop=stop,                                               
            num=steps,                                               
            endpoint=False,                                          
        )                                                            
                                                                     
        # This adjustment could be externalized                      
        nonlinear_adjustment = nonlinearity(self.linear_grid)        
        self.nonlinear_grid = self.linear_grid + nonlinear_adjustment
                                                                     
        # Normalize the nonlinear grid based on the measure duration.
        self.nonlinear_grid /= 2 * np.pi / measure_duration_s        
                                                                     
        self.df = pd.DataFrame({"start": self.nonlinear_grid})       
```


<img src="/algrtm-blog/assets/Hello-MIDI/pianoroll-a.png" alt="pianoroll" style="height: 170px; display: block; float: left;">
<div style="clear: both;"></div>
<audio controls>
  <source src="/algrtm-blog/assets/Hello-MIDI/pianoroll-a.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

Finally, some GPT created text:

While AI systems, such as machine learning models, can generate content that mimics patterns they've learned from vast amounts of data,
**they fundamentally** lack the intrinsic human qualities that drive creativity. True creativity often emerges from a complex interplay of emotions, lived experiences, cultural contexts, and deeply personal insights. It's shaped by our struggles, joys, dreams, and even our subconscious minds. These aspects of the human experience are intricately woven into the tapestry of our creative expressions. In contrast, AI operates devoid of emotion, consciousness, or a sense of self. It lacks intuition and the ability to derive meaning or feel inspiration. An AI can replicate styles, combine patterns, or optimize based on predefined criteria, but it does so without understanding, intent, or genuine innovation. Thus, while AI can produce or assist in artistic endeavors, it will never be "creative" in the profoundly human sense of the word.