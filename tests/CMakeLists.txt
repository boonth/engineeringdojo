file(GLOB TEST_SOURCES *.c)
include_directories(${CMAKE_SOURCE_DIR}/src) #for newtan.h
if(ENABLE_TESTING)
  add_executable(mytest ${TEST_SOURCES})
  target_link_libraries(mytest mym)

  add_test (TestRuns mytest 1)

  add_test (Test2 mytest 2)
  
  add_test (Test3 mytest)
  set_tests_properties(Test3 PROPERTIES WILL_FAIL TRUE)
  
  set_tests_properties (Test2 PROPERTIES PASS_REGULAR_EXPRESSION "-2.185")
endif(ENABLE_TESTING)

