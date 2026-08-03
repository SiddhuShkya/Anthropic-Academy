# Introducing Tool Use

**Tool use** = a method for Claude to access external information beyond its training data.

## The Default Limitation

Claude only knows what's in its training data — it lacks current, real-time information.

## Tool Use Flow

1. Send an initial request to Claude, plus instructions for accessing external data
2. Claude evaluates whether external data is needed, and requests specific information
3. The server runs code to fetch the requested data from an external source
4. A follow-up request is sent to Claude, including the retrieved data
5. Claude generates a final response using the original prompt + external data

## Example: Weather

User asks about current weather → Claude requests weather data → server calls a weather API → Claude receives the data → Claude gives an informed, current answer.

## Key Concept

Tools let Claude augment its responses with live/current information by orchestrating external data retrieval between its own requests.
