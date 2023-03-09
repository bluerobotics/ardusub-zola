<div class="simple" style="display:none;padding-bottom:15px;{% if center %}text-align:center;{% endif %}">

<img src="{{ src }}-simple.png" alt="{{ src | replace(from="-", to=" ") | title }} (simple mode)" {% if width %}width={{ width }}{% endif %} {% if height %}height={{ height }}{% endif %}>

</div>

<div class="pirate" style="display:block;padding-bottom:15px;{% if center %}text-align:center;{% endif %}">

<img src="{{ src }}-pirate.png" alt="{{ src | replace(from="-", to=" ") | title }} (pirate mode)" {% if width %}width={{ width }}{% endif %} {% if height %}height={{ height }}{% endif %}>

</div>
