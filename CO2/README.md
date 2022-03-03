
Clone this repository "https://github.com/SimulationEverywhere-Models/Cadmium-CellDEVS-SampleModels.git"

In CMakeLists.txt add few lines

1) file(MAKE_DIRECTORY simulation_results)
2) include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../../cadmium-web-extension/include) on line 9.
3) add_executable(co2_lab CO2/model/co2_main.cpp)
4) target_link_libraries(co2_lab  Boost::program_options)

Below changes made in this model to be compatible with the new Cadmium and Web-Viewer
In co2_main.cpp

1) #include <web/web_results.hpp> see line 37.
2) std::vector<std::string>fields = { "counter", "concentration", "type" };  //should match the output fields
   web::convert_cell_devs(fields, scenario_config_file_path,"./simulation_results/state.txt","./simulation_results/");

In co2__lab_cell.hpp

1) change the format of the output it should be - os << x.counter << "," << x.concentration << "," << x.type; (see line 66)

Format of the scenario file (see example, config_vsim.json)

To run:
 Compile using cmake:

a) open the bash prompt in the Cadmium-CellDEVS-SampleModels folder and execute this command, cmake ./
b) this will create a makefile in the folder, now execute make
c) this will create the executable co2_lab in the bin folder
d) now run command, ./bin/co2_lab ./CO2/config_vsim.json 500

The simulationresults folder will be populated with 3 files once the simulation starts running, messages.log, structure.json and style.json.

To link to the Web-viewer to see the results "https://staubibr.github.io/app-simple/index.html". (upload all three files messages.log, structure.json and style.json)

For more info, read "https://github.com/SimulationEverywhere/cadmium-web-extension/blob/b8634d2028be09070f67a713920c4fc3121ea89d/Instructions.docx" for the Cell-DEVS model at the end.