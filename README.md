# django-bootstrap-datetimepicker

This package includes a Django widget for displaying date pickers with Bootstrap 4. It uses [Bootstrap datepicker widget version 1.10 ](https://github.com/uxsolutions/bootstrap-datepicker).

## Install

    pip install django-bootstrap-datepicker

Make sure to add `bootstrap_datepicker` to your `INSTALLED_APPS`. Then run `manage.py collectstatic` to include the bootstrap-datepicker js and css files.

## New

Updated to 1.10 of Bootstrap-datepicker

## Example

#### forms.py

```python
from bootstrap_datepicker.widgets import DatePicker
from django import forms

class ToDoForm(CreateView):
    fields = ("testdate")
    .......

    def get_form(self, form_class=None):
    .......
    form.fields['testdate'].widget =  DatePicker(
        options={
            "format": "mm/dd/yyyy",
            "autoclose": True,
            "daysOfWeekDisabled": "0,6"
        }
    )
```

The `options` will be passed to the JavaScript datepicker instance, and are documented and demonstrated here:

* [Bootstrap Datepicker Documentation](https://bootstrap-datepicker.readthedocs.org/en/stable/) (ReadTheDocs.com)
* [Interactive Demo Sandbox of All Options](https://uxsolutions.github.io/bootstrap-datepicker/)

You don't need to set the `language` option, because it will be set the current language of the thread automatically.

#### template.html

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="{% static 'contrib/bootstrap.css' %}">
    <link rel="stylesheet" href="{% static 'contrib/font-awesome.min.css' %}">
    <script src="{% static 'contrib/bootstrap.js' %}"></script>
    {{ form.media }}
  </head>
  <body>
    <form method="post" role="form">
      {% csrf_token %}
      {{ form|crispy }}
      <div class="form-group">
        <input type="submit" value="Submit" class="btn btn-primary" />
      </div>
    </form>
  </body>
</html>
```

Here we assume you're using [django-crispy-forms]https://github.com/django-crispy-forms/django-crispy-forms.

## Requirements

* Python >= 3.9
* Django >= 4.0
* Bootstrap >= 4.0
* jquery >= 3.4.0
* font-awesome >= 4.5.X
