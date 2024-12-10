---
{% if states('sensor.seventeentrack_packages_in_transit') == '0' %} Es existieren derzeit keine Lieferungen.
{% else %}
{% for package in states.sensor.seventeentrack_packages_in_transit.attributes.packages %}

### 📦 **{{ package.friendly_name }}**
**Tracking-Nummer:** [{{ package.tracking_number }}](https://www.dhl.de/de/privatkunden/pakete-empfangen/verfolgen.html?piececode={{package.tracking_number }})
**Datum:** {{ as_timestamp(package.timestamp) | timestamp_custom('%d.%m.%Y – %H:%M') }} Uhr {% set info_text = package.info_text %}
  {% if info_text == "The shipment has been loaded onto the delivery vehicle" %} Die Sendung wurde in das Zustellfahrzeug geladen.
  {% elif info_text == "The shipment has been processed in the parcel center of origin" %} Die Sendung wurde im Ursprungspaketzentrum bearbeitet.
  {% elif info_text == "The shipment arrived in the region of recipient and will be transported to the delivery base in the next step." %} Die Sendung ist in der Empfängerregion angekommen und wird im nächsten Schritt zur Zustellbasis transportiert.
  {% elif info_text == "The shipment has been processed in the parcel center of origin" %} Die Sendung wurde im Ursprungspaketzentrum bearbeitet.
  {% elif info_text == "Pick-up was successful" %} Die Sendung wurde abgeholt.
  {% elif info_text == "The shipment has been posted by the sender at the retail outlet" %} Die Sendung wurde vom Absender in der Filiale eingeliefert.
  {% elif info_text == "The instruction data for this shipment have been provided by the sender to DHL electronically "%} Die Auftragsdaten für diese Sendung wurden vom Absender elektronisch an DHL übermittelt.
  {% elif info_text == "Departed from facility" %} Einrichtung verlassen.
  {% elif info_text == "The parcel data was entered into GLS IT system; the parcel was not yet handed over to GLS" %} Die Paketdaten wurden in das IT-System von GLS eingegeben; das Paket wurde noch nicht an GLS übergeben.
  {% elif info_text == "CHINA, SHENZHEN, Departed Sunyou Facility" %} CHINA, SHENZHEN, Verlassen der Sunyou-Anlage
  {% elif info_text == "Pre-Shipment Info Sent to Germany" %} Informationen vor dem Versand nach Deutschland gesendet
  {% elif info_text == "In transit." %} Auf dem Transportweg
  {% elif info_text == "CHINA, SHANGHAI, Acceptance, Sent to Germany" %} CHINA, SHANGHAI, Abnahme, Versand nach Deutschland
  {% elif info_text == "HONG KONG, Departed HONG KONG Airport" %} HONGKONG, Abflug vom Flughafen HONGKONG
  {% elif info_text == "Germany, Arrived at Destination Country Airport" %} Deutschland, Ankunft am Flughafen des Ziellandes
  {% elif info_text == "GMTC, Arrived" %} GMTC, In Transitland angekommen.
  {% elif info_text == "GMTC, Departed" %} GMTC, In Transitland abgefahren. 
  {% elif info_text == "Out for delivery." %} Zur Auslieferung bereit.
  {% elif info_text == "Yanwen facility - Outbound" %} Yanwen-Einrichtung - Ausgehend
  {% elif info_text == "Export customs clearance complete, Carrier note: Export clearance success" %} Exportverzollung abgeschlossen
  {% elif info_text == "飞机进港" %} Das Flugzeug kam am Einreiseflughafen an.
  {% elif info_text == "Arrived at customs, Carrier note: Arrived at customs" %} Angekommen beim Zoll
  {% elif info_text == "Departed from transit country/region, Carrier note: Depart from transit country or district" %} Abgereist aus Transitland/-region
  {% elif info_text == "Port of departure - Departure" %} Abfahrtshafen – Abflug
  {% elif info_text == "International shipment release - Import" %} Freigabe der internationalen Sendung – Einfuhr
  {% elif info_text == "delivery to courier" %} Lieferung an Kurier
  {% elif info_text == "您的邮件已通过欧盟海关的审核，发往下环节处理" %} Ihre Sendung hat die EU-Zollprüfung bestanden und wird an den nächsten Partner zur Bearbeitung weitergeleitet.
  {% elif info_text == "Batch delivery to carrier" %} Lieferung an den Spediteur.
  {% elif info_text == "【广东省深圳市国际互换局】已出口直封" %} Die Sendung hat das Verteilzentrum verlassen und wird an Shenzhen International gesendet.
  {% elif info_text == "航空公司接收" %} Die Fluggesellschaft hat die Sendung erhalten.
  {% elif info_text == "到达寄达地" %} Ankunft am Zustellort
  {% elif info_text == "Arrived at departure transport hub, Carrier note: Arrived at departure transport hub" %} Angekommen im Abflug-Transportzentrum
  {% elif info_text == "Order data transmitted electronically." %} Auftragsdaten wurden elektronisch übermittelt.
  {% elif info_text == "Leaving from departure country/region, Carrier note: Leaving from departure country/region" %} Abflug aus Abgangsland/-region
  {% elif info_text == "Departed from departure country/region, Carrier note: Left from departure country/region" %} Abgereist aus Abgangsland/-region
  {% elif info_text == "Import customs clearance complete, Carrier note: Import customs clearance complete" %} Einfuhrzollabfertigung abgeschlossen
  {% elif info_text == "Awaiting for transit to final delivery office, Carrier note: Package arrived at facility of the local delivery company" %} Das Paket ist in der Einrichtung des örtlichen Zustellunternehmens angekommen
  {% elif info_text == "Parcel center of origin." %}  Paketketzentrum des Herkunftsorts
  {% elif info_text == "Preparation for onward transport" %} Vorbereitung für den Weitertransport
  {% elif info_text == "Original" %} Übersetzung
  {% elif info_text == "Original" %} Übersetzung
  {% else %}{{ package.info_text }} {% endif %} {% set location = package.location %} {% if location == "Germany" %} Deutschland
  {% elif location == "深圳市" %} Shenzhen (China)
  {% elif location == "Original" %} Übersetzung
  {% elif location == "Original" %} Übersetzung {% else %} {{ package.location }} {% endif %}

---

{% endfor %}
{% endif %}
