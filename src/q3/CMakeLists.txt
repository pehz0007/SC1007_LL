
add_executable(Q3 Q3.c)

function(CREATE_TEST TEST_NAME)
    add_test(NAME ${TEST_NAME} COMMAND sh -c "\"$<TARGET_FILE:Q3>\" < \"${CMAKE_SOURCE_DIR}/tests/q3/${TEST_NAME}_input.txt\"")
    file(READ "${CMAKE_SOURCE_DIR}/tests/q3/${TEST_NAME}_output.txt" EXPECTED_OUTPUT_CONTENT)
    string(REPLACE "\n" "[\r\n\t ]*" EXPECTED_OUTPUT_CONTENT "${EXPECTED_OUTPUT_CONTENT}")
    set_tests_properties(${TEST_NAME} PROPERTIES PASS_REGULAR_EXPRESSION "${EXPECTED_OUTPUT_CONTENT}")
endfunction()

create_test(Q3_EMPTY_LIST)
create_test(Q3_EVEN_LIST)
create_test(Q3_ODD_LIST)

create_test(Q3_INPUT1_LIST)
create_test(Q3_INPUT2_LIST)