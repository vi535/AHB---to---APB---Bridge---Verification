# AHB-to-APB Bridge Verification
Overview
This project verifies an AHB-to-APB bridge using a Universal Verification Methodology (UVM) testbench implemented in SystemVerilog. The AHB-to-APB bridge facilitates data transfers between a high-speed Advanced High-performance Bus (AHB) master and low-power Advanced Peripheral Bus (APB) slaves, adhering to AMBA protocol specifications. Developed as part of advanced VLSI verification training at Maven Silicon (May 2024–Feb 2025), this project demonstrates proficiency in SystemVerilog, UVM, and industry-standard tools like Synopsys VCS and Verdi.
Features

Constrained-Random Testing: Generates diverse AHB transaction scenarios, including single transfers, incremental bursts, and error conditions.
Scoreboarding: Verifies data integrity between AHB master and APB slave transactions.
Functional Coverage: Achieved 95% coverage, validating key protocol features like burst transfers and APB addressing.
Assertions: Ensures protocol compliance (e.g., AHB HTRANS, APB PSEL signals).
Simulation and Debugging: Simulated using Synopsys VCS and Mentor QuestaSim, with signal-level debugging via Synopsys Verdi.

Project Structure
AHB-to-APB-Bridge-Verification/
├── src/                    # DUT and testbench code
│   ├── ahb_apb_bridge.v    # AHB-to-APB bridge DUT (Verilog)
│   ├── tb_top.sv           # UVM testbench top module
│   ├── ahb_if.sv           # AHB interface
│   ├── apb_if.sv           # APB interface
│   ├── driver.sv           # UVM driver
│   ├── monitor.sv          # UVM monitor
│   ├── scoreboard.sv       # UVM scoreboard
│   ├── sequence.sv         # UVM sequence
│   ├── test.sv             # UVM test
├── scripts/                # Simulation scripts
│   ├── run_vcs.sh          # VCS simulation script
│   ├── run_questa.sh       # QuestaSim simulation script
├── docs/                   # Documentation
│   ├── test_plan.pdf       # Test plan with test cases
│   ├── coverage_report.pdf # Coverage analysis report
├── waveforms/              # Simulation waveforms
│   ├── burst_transfer.png  # AHB burst transfer waveform
│   ├── error_scenario.png  # APB error scenario waveform
├── README.md               # This file

Setup and Simulation

Clone the Repository:
git clone https://github.com/VinayKakarla/AHB-to-APB-Bridge-Verification.git


Install Tools: Ensure Synopsys VCS, Mentor QuestaSim, or compatible simulators are installed.

Run Simulation:
cd scripts
./run_vcs.sh  # For VCS
./run_questa.sh  # For QuestaSim


View Waveforms: Open waveforms in Synopsys Verdi or QuestaSim for debugging (e.g., waveforms/burst_transfer.png).


Testbench Architecture
The UVM testbench includes:

Driver: Drives AHB transactions (e.g., HADDR, HWDATA) and APB signals (e.g., PADDR, PWDATA).
Monitor: Captures AHB and APB transactions for analysis.
Scoreboard: Compares AHB input transactions with APB output transactions to ensure data integrity.
Sequence: Generates constrained-random stimuli, including single transfers, 4-beat bursts, and error cases.
Coverage Model: Tracks functional coverage for AHB HTRANS types, APB PSEL states, and transaction types.
Assertions: Validates protocol timing (e.g., AHB HREADY, APB PENABLE).

Key Results

Coverage: Achieved 95% functional coverage and 90% code coverage, covering all major AHB/APB transaction types.
Bugs Identified: Fixed 3 critical bugs, including incorrect APB PSEL timing and AHB burst transfer errors.
Debugging: Used Synopsys Verdi to resolve signal-level issues, such as metastability in clock domain crossing.

Challenges and Solutions

Challenge: AHB burst transfer errors due to incorrect scoreboard comparison.
Solution: Modified scoreboard to handle incremental burst data correctly, verified via Verdi waveform analysis.
Challenge: Incomplete coverage of APB error scenarios.
Solution: Added directed tests for PSLVERR conditions, increasing coverage to 95%.

Tools and Technologies

Simulation: Synopsys VCS, Mentor QuestaSim, Synopsys Verdi
Linting: Synopsys SpyGlass
Languages: SystemVerilog, Verilog
Methodology: UVM, Assertion-Based Verification
Protocols: AHB, APB (AMBA)

Waveforms
Below is a sample waveform showing a 4-beat AHB burst transfer:
Future Enhancements

Add support for AHB wrap bursts and additional APB slaves.
Integrate power-aware verification using UPF (Unified Power Format).
Extend testbench for multi-master AHB configurations.

License
MIT License
Contact
Vinay KakarlaEmail: kvinay5558@gmail.comLinkedIn: Your LinkedIn ProfileGitHub: Your GitHub Profile
