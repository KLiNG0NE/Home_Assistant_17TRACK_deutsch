---
{% if states('sensor.seventeentrack_packages_ready_to_be_picked_up') == '0' %} Dezeit sind keine Pakete zur Abholung vorgesehen.
{% else %}
{% for package in states.sensor.seventeentrack_packages_ready_to_be_picked_up.attributes.packages %}

### 📦 **{{ package.friendly_name }}**
**Trackingnummer:** [{{ package.tracking_number }}](https://www.dhl.de/de/privatkunden/pakete-empfangen/verfolgen.html?piececode={{package.tracking_number }})
**Datum:** {{ as_timestamp(package.timestamp) | timestamp_custom('%d.%m.%y %H:%M') }} Uhr.{% set info_text = package.info_text %}
{% if info_text == "Ready to be Picked Up" %} Bereit zur Abholung
{% elif info_text == "Out for delivery." %} Zur Auslieferung bereit.
{% elif info_text == "Out for delivery, Carrier note: Out for delivery" %} Zur Auslieferung bereit.
{% elif info_text == "Original" %} Übersetzung
{% elif info_text == "Original" %} Übersetzung
{% elif info_text == "Original" %} Übersetzung
{% else %}{{ package.info_text }}{% endif %}
{{ package.location }}

---

{% endfor %}
{% endif %}
