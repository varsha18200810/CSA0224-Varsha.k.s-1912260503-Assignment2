#include <stdio.h>
static int calls;
static int verify_card(int id) { ++calls; return id % 20 == 0; }
int main(void) {
    int senior, eligible, id, concession;
    calls = 0;
    for (id = 0; id < 1000; ++id) {
        senior = (id < 200);
        eligible = (id % 10 < 6);
        concession = (senior && eligible) || verify_card(id);
        (void)concession;
    }
    printf("Verification calls = %d\n", calls);
    return 0;
}

