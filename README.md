# Flying-Ad-hoc-Networks

## Prerequisites

Before starting, ensure the following requirements are met:

1. **Operating System**: Ubuntu 20.04 or later
2. **Tools**:
   - Wireshark (installed and configured)
   - FANET simulation software (e.g., NS-3, OMNeT++, or other FANET simulation tools)
   - Python (optional, for data analysis scripts if needed)
3. **Network Configuration**: Ensure proper network privileges to capture and analyze packets using Wireshark.

## Step 1: Install Dependencies

1. Update the system:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. Install Wireshark:
   ```bash
   sudo apt install wireshark -y
   ```

   > **Note**: During installation, select 'Yes' when prompted to allow non-superusers to capture packets.

3. Install simulation tools (example: NS-3):
   ```bash
   sudo apt install ns3 -y
   ```

   Alternatively, follow the official installation guide for your chosen simulation tool.

4. (Optional) Install Python and libraries for data analysis:
   ```bash
   sudo apt install python3 python3-pip -y
   pip3 install pandas matplotlib
   ```

## Step 2: Set Up FANET Simulation

1. Clone or prepare your FANET simulation scripts:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Configure the simulation environment:
   - Edit configuration files (if applicable) to set parameters such as network topology, node mobility, and transmission ranges.
   - Example configuration file:
     ```
     # fanet_config.json
     {
         "nodes": 10,
         "range": 100,
         "mobility_model": "RandomWaypoint",
         "duration": 300
     }
     ```

3. Run the simulation:
   ```bash
   ./run_simulation.sh
   ```

   Refer to the simulation tool’s documentation if specific commands are needed.

## Step 3: Capture and Analyze Packets with Wireshark

1. Start Wireshark:
   ```bash
   wireshark
   ```

2. Select the appropriate network interface:
   - Choose the virtual interface or loopback interface corresponding to the FANET simulation.

3. Start capturing packets:
   - Click the green ‘Start Capturing’ button.
   
4. Analyze packets:
   - Use filters such as `ip.src` or `udp.port` to focus on specific traffic.
   - Example filter:
     ```
     udp.port == 5000
     ```

5. Save the captured packets:
   - Go to **File > Save As** and save the capture as a `.pcap` file for future analysis.

## Step 4: Visualize and Interpret Data

1. Use Wireshark’s statistics tools:
   - Navigate to **Statistics > Protocol Hierarchy** to view protocol distribution.
   - Use **Statistics > I/O Graphs** to plot traffic trends.

2. (Optional) Export packet data to CSV:
   - Go to **File > Export Packet Dissections > As CSV**.

3. Analyze the CSV using Python (if needed):
   ```python
   import pandas as pd
   data = pd.read_csv("packets.csv")
   print(data.head())
   ```

## Step 5: Generate Reports

1. Summarize results:
   - Include key findings such as packet loss, latency, and throughput.
   - Highlight unusual patterns or issues observed during the simulation.

2. Export visualizations:
   - Use tools like Matplotlib or export graphs from Wireshark for inclusion in reports.

## Troubleshooting

1. **Wireshark permissions issue**:
   - Add your user to the Wireshark group:
     ```bash
     sudo usermod -aG wireshark $USER
     ```
   - Log out and back in for the changes to take effect.

2. **Simulation errors**:
   - Ensure all dependencies for the simulation tool are installed.
   - Check log files for detailed error messages.

3. **Packet capture issues**:
   - Verify that the correct network interface is selected in Wireshark.
   - Ensure sufficient permissions are granted.

## Conclusion

Follow these steps to successfully run your FANET simulation and analyze network traffic. Use this guide as a reference for setting up and troubleshooting the project environment.

