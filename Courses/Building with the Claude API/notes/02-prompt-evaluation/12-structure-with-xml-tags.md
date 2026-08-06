# Structure with XML Tags

Using XML tags to organize and delineate different content sections within a prompt, improving the AI's comprehension.

## Purpose

When interpolating large amounts of content into a prompt, XML tags help the model distinguish between different types of information and understand where each section begins/ends.

## Implementation

Wrap content sections in descriptive tags, e.g.:

```xml
<sales_records>
...
</sales_records>

<my_code>
...
</my_code>
```

## Tag Naming

Use descriptive, specific names — `sales_records` is far more useful than a generic `data`.

## Example Use Case

A debugging prompt mixing code and documentation becomes much clearer once separated:

```xml
<my_code>...</my_code>
<docs>...</docs>
```

## Benefits

- Makes the prompt's structure obvious to the model
- Reduces confusion about content boundaries
- Improves output quality — even for smaller blocks of content

## Application

Wrap any interpolated content — even something short, like `<athlete_information>` — to clarify that it's external input the model needs to consider.
