# 🤖 Progent

Progent: Your ArcGIS Pro Trusted Agent for intelligent GIS data analysis through natural language conversation.

## ✨ Features

- 🧠 **AI Support**: Google Gemini
- 💬 **Natural Language Interface**: Chat with your GIS data in Arabic or English
- 🔧 **Comprehensive GIS Toolkit**: A wide range of spatial analysis capabilities executed on the client.
- 🌐 **Decoupled Architecture**: A FastAPI server for AI orchestration and a separate ArcGIS Pro client for all `arcpy` execution, communicating via WebSockets.
- 📊 **Investigation Mode**: AI chains multiple analyses for comprehensive insights.

## 📁 Project Structure

The project is divided into two main components: the server-side application (`app/`) and the ArcGIS Pro client (`AddIn/`).

- **`app/`**: The core FastAPI web server.
  - `main.py`: The main entry point for the FastAPI server.
  - `langchain_agent.py`: The AI agent responsible for understanding user queries and orchestrating function calls.
  - `websocket_manager.py`: Manages the WebSocket communication between the server and the ArcGIS Pro client.
  - `ai/function_declarations.py`: Contains the function signatures that the AI uses to understand the available tools. This acts as a "manual" for the AI, but contains no executable code.

- **`AddIn/`**: The ArcGIS Pro Add-in (the client).
  - `progent.pyt`: A Python Toolbox that contains all the GIS-specific functions using `arcpy`. This is where all the actual GIS work happens.
  - `WebSocketService.cs`: The C# service that runs within ArcGIS Pro, handling the WebSocket connection and executing functions in `progent.pyt` based on messages from the server.

- **`static/` & `templates/`**: The web UI for the chat interface.

##  architectural-principle

The server application (`app/`) is designed to be completely decoupled from the ArcGIS Pro client (`AddIn/`). The server's role is to manage the AI, handle user interactions, and pass messages to the client. It has no knowledge of how the GIS functions are implemented and contains no `arcpy` code. All GIS-specific logic and execution are handled exclusively by the client running within ArcGIS Pro.

## 🔧 Available AI Models

- **Gemini Flash** ⚡ (Recommended - Fast & Free)
- **Gemini Pro** 🧠 (Advanced reasoning)

## 🗺️ GIS Analysis Functions

The assistant provides over 60 built-in spatial analysis functions:

- **Chart Management**: Add, update, delete, and rearrange dashboard charts with flexible layout controls.
- **Field Insights**: Summarize field statistics, sample values, and generate data stories for each attribute.
- **Spatial Selection**: Select features by attribute, location, or proximity.
- **Geometric Analysis**: Calculate area, length, centroids, and buffers.
- **Spatial Operations**: Perform clipping, spatial joins, and nearest neighbor analysis.
- **Raster Analysis**: Execute raster calculations, reclassify values, extract statistics, and perform map algebra on raster datasets.
- **Dashboard Generation**: Automatically create smart dashboards for any GIS layer, selecting the most insightful fields and visualizations.
- **Layout Customization**: Update dashboard grid layouts and chart arrangements.

## 🛠️ Troubleshooting

| Problem | Solution |
|---------|----------|
| Server won't start | Run `setup_environment.bat` |
| API errors | Check API keys in `.env` file or submit api key via chatbot api inputs |
| ArcGIS connection fails | Verify server `.start_server.bat` is up and running |
| Function errors | review `system.log` |

## 📋 System Requirements

- Windows 10/11
- Python 3.8+
- Internet connection (for AI APIs)
- ArcGIS Pro 3.2+

## 🚀 Installation

For step-by-step setup instructions, please see [installation_guide.txt](./installation_guide.txt).

## 📜 License
This project is open source and licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0). You are free to use, modify, and distribute the code, provided you comply with the terms of the license. Please also ensure compliance with AI provider terms of service.
