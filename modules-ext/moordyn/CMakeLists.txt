#
# Copyright 2016 National Renewable Energy Laboratory
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

generate_f90_types(src/MoorDyn_Registry.txt MoorDyn_Types.f90)

set(MOORDYN_LIBS_SOURCES
  src/MoorDyn.f90
  src/MoorDyn_IO.f90

  # Generated files
  MoorDyn_Types.f90)

add_library(moordynlib ${MOORDYN_LIBS_SOURCES})
target_link_libraries(moordynlib nwtclibs)

install(TARGETS moordynlib
  EXPORT "${CMAKE_PROJECT_NAME}Libraries"
  RUNTIME DESTINATION lib
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib)
