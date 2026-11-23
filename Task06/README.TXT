#include <stdio.h>
int main(void) {
    double principal, rate, repayment, balance, total_interest = 0.0;
    int month = 0, limit = 360;
    printf("Enter principal, monthly rate (percent), repayment: ");
    if (scanf("%lf %lf %lf", &principal, &rate, &repayment) != 3 || principal <= 0 || rate < 0 || repayment <= 0) {
        puts("Invalid input."); return 1;
    }
    balance = principal; rate /= 100.0;
    while (balance > 0.005) {
        double interest = balance * rate;
        double due = balance + interest;
        double payment;
        if (repayment <= interest) { puts("Repayment does not exceed monthly interest; loan will not reduce."); return 0; }
        payment = repayment < due ? repayment : due;
        balance = due - payment;
        if (balance < 0.005) balance = 0.0;
        total_interest += interest; ++month;
        printf("%3d  interest=%10.2f payment=%10.2f balance=%10.2f\n", month, interest, payment, balance);
        if (month >= limit && balance > 0.005) { puts("Safety limit reached; loan remains unpaid."); break; }
    }
    if (balance <= 0.005) printf("Repaid in %d months; total interest=Rs %.2f\n", month, total_interest);
    return 0;
}

