# Routing Workflows

A workflow pattern that **categorizes** user input to determine the appropriate processing pipeline.

## Key Mechanism

An initial request to Claude categorizes the user's input into predefined genres/categories. Based on that categorization, the system routes the request to a specialized processing pipeline with customized prompts/tools.

## Example Flow

1. User enters a topic (e.g., "Python functions")
2. Claude categorizes the topic (e.g., "educational")
3. The system uses an educational-specific prompt template
4. Claude generates a script with an educational tone/structure

## Benefits

Ensures the output matches the nature of the topic:
- Programming topics get an educational treatment, with definitions/explanations
- Entertainment topics get trendy language and engaging hooks

## Structure

```
One routing step → Multiple specialized processing pipelines
                    (each with customized prompts/tools for its category)
```

## Use Case

Social media video-script generation, where different topics require very different tones and approaches.
