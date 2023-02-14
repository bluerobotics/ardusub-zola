<div {% if class %}class="{{class}}" style="display:{% if class == "pirate" %}block{% else %}none{% endif %};{% else %}style="{% endif %}padding-bottom:15px;{% if center %}text-align:center;{% endif %}">

<img src="{{ src }}.png" alt="{% if alt %}alt{% else %}{{ src | replace(from="-", to=" ") | title }}{% endif %}{% if alt_extra %}{{ alt_extra }}{% endif %}" {% if width %}width={{ width }}{% endif %} {% if height %}height={{ height }}{% endif %}>

</div>
