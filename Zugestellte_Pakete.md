---
{% for package in states.sensor.seventeentrack_packages_delivered.attributes.packages %}

### 📦 **{{ package.friendly_name }}**
**Trackingnummer:** [{{ package.tracking_number }}](https://www.dhl.de/de/privatkunden/pakete-empfangen/verfolgen.html?piececode={{package.tracking_number}})
**Datum:** {{ as_timestamp(package.timestamp) | timestamp_custom('%d.%m.%y – %H:%M') }} Uhr{% set info_text = package.info_text %}
{% if info_text == "The shipment has been successfully delivered" %} Die Lieferung wurde erfolgreich zugestellt.
{% elif info_text == "Delivered." %} Geliefert
{% elif info_text == "Delivery successful."%} Die Zustellung war erfolgreich. 
{% elif info_text == "The recipient has picked up the shipment from the retail outlet" %} Der Empfänger hat die Sendung in der Verkaufsstelle abgeholt.
{% elif info_text == "Delivered., Evidence" %} Auslieferung bestätigt
{% elif info_text == "Package delivered, Carrier note: Package delivered" %} Paket wurde geliefert.
{% elif info_text == "Original" %} Übersetzung
{% elif info_text == "Original" %} Übersetzung
{% elif info_text == "Original" %} Übersetzung
{% else %} {{package.info_text}}
{% endif %} {% set location = package.location %} {% if location == "Germany" %} Deutschland
{% elif location == "Allemagne" %} Deutschland
{% elif location == "Alemania" %} Deutschland
{% elif location == "德国" %} Deutschland
{% elif location == "Original" %} Übersetzung
{% elif location == "Original" %} Übersetzung
{% elif location == "Original" %} Übersetzung
{% else %} {{ package.location }}
{% endif %}

---

{% endfor %}
