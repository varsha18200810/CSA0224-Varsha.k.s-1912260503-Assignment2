#include <stdio.h>
unsigned long tests;
int is_prime_odd_optimised(unsigned long n) {
    unsigned long i; tests = 0;
    if (n < 2) return 0;
    if (n == 2) return 1;
    ++tests; if (n % 2 == 0) return 0;
    for (i = 3; i <= n / i; i += 2) {
        ++tests; if (n % i == 0) return 0;
    }
    return 1;
}
int main(void) {
    unsigned long values[] = {97, 100, 7919, 1000003};
    for (int k=0; k<4; ++k) {
        int result = is_prime_odd_optimised(values[k]);
        printf("%lu %s tests=%lu\n", values[k], result ? "prime" : "not prime", tests);
    }
    return 0;
}
