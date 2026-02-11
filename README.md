# NYCTAXIProblem Statement

Taxi demand in NYC shifts every few minutes across zones, but most decisions today are reactive.

Drivers guess where to find the next ride

Fleet operators lack visibility into demand movement

Aggregators cannot proactively manage distribution or pricing

15+ years of TLC trip data is rarely used for real-time operational intelligence

What’s missing is a zone-level demand prediction system that can power positioning, allocation, and pricing decisions before demand spikes.

What This Project Does

This project builds a batch + streaming ML system that predicts which NYC taxi zones will be busiest in the next 15 minutes.

Processes historical TLC data with PySpark

Creates spatiotemporal features at (zone, 15-min window)

Trains a ML model to predict future trip counts per zone

Uses Kafka to simulate live trip streams

Runs PySpark Structured Streaming for real-time inference

Continuously outputs live hotspot zones

Displays predictions on a NYC map in real time 🗺️

This can be used by:

🚖 Drivers for positioning

🚚 Fleet operators for allocation

📈 Aggregators for pricing & surge strategy

🏙️ City planners for mobility insights

How to Run
1️⃣ Train the Model
cd "ML Pipeline"
spark-submit NYCHotspotPrediction.py

2️⃣ Start Kafka
kafka-topics --create --topic taxi_stream --bootstrap-server localhost:9092

3️⃣ Start Producer (Simulated Live Data)
cd Producer
python TaxiDataStream.py

4️⃣ Start Consumer (Real-Time Prediction)
cd Consumer
spark-submit HotspotConsumer.py

Output

The system continuously predicts hotspot zones and plots them on the NYC map in real time.

🟢 Predicted hotspots
🔴 Actual hotspots
🟣 Correct predictions

(See newplot.png for sample output)

Tech Stack

Data & ML: PySpark, PySpark MLlib, Pandas, GeoPandas
Streaming: Apache Kafka, PySpark Structured Streaming
Visualization: Plotly, Matplotlib
Language: Python