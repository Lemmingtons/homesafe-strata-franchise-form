# Homesafe Strata Franchise Form

Static GitHub Pages form for Homesafe Strata Inspections franchise applications.

The page mirrors the existing Homesafe franchise form layout and uses the Strata application questions from `HSI Strata Franchisee Application Form.docx`.

## HubSpot

Set `HUBSPOT_FORM_ENDPOINT` in `index.html` once the Strata HubSpot form is created.

Expected endpoint shape:

```text
https://forms.hubspot.com/uploads/form/v2/47894346/<STRATA_FORM_ID>
```

Do not reuse the Building & Pest franchise form ID unless the intention is to mix Strata applications into that form.
