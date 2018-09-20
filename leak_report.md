# Leak report

The memory leak occurs in the `char* strip(char* str)` function. The `result` variable allocates space on line 41 with `calloc` and since `report` is a return value, the memory leak is passed onto `cleaned` in the `int is_clean(char* str)` function (`cleaned` is the result of `strip(str)`). So in order to fix this, `cleaned` just needs to be freed. However, if the length of `cleaned` is 0, an invalid pointer error will appear. So I just put `free(cleaned)` in an if statement to check that `cleaned` isn't 0. 

