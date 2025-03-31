---
title: Hardware
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---
  
<!--more-->

The battery supplies power to the box. Inside the box, the power is directed from the power input to the step-down converter. A step-down converter reduces the input voltage of an unregulated DC power supply to a stabilized, lower output voltage. The step-down converter is connected to the Raspberry Pi via USB. Also from the power input, this time via a step-up converter, the input voltage is converted to a higher output voltage to provide enough power for the LED lamps to function as a flash for the photos. A relay is located between the input and the step-up converter, as well as between the step-up converter and the LED lamps. This allows for power management to safely input and output it. The relay is important to protect the electrical system from excessive voltage or current and to ensure the safe operation of all connected devices, thereby reducing the risk of electrical interference and minimizing potential malfunctions.

{% include figure image_path="/assets/images/unit_images/unit06/Components.png"=x150 caption="List of components." %}
{% include figure image_path="/assets/images/unit_images/unit06/Hardware-in-box.png" caption="Components of the sensor box." %}

