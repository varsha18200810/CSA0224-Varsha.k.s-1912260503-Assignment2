#include <stdio.h>
int main(void) {
    double price, gross, discount, taxable, gst, total, net;
    int qty, senior;
    printf("Enter unit price, quantity and senior flag (0/1): ");
    if (scanf("%lf %d %d", &price, &qty, &senior) != 3 || price < 0 || qty < 0       (senior != 0 && senior != 1)) {
        puts("Invalid input."); return 1;
    }
    gross = price * qty;
    discount = senior ? gross * 0.15 : 0.0;
    taxable = gross - discount;
    gst = taxable * 0.05;
    total = taxable + gst;
    net = total > 1000.0 ? total - 50.0 : total;
    printf("Gross=Rs %.2f\nDiscount=Rs %.2f\nGST=Rs %.2f\nTotal=Rs %.2f\nNet=Rs %.2f\n", gross, discount, gst, total, net);
    return 0;
}

