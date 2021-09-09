# assignment2-Tumee
second assignment repository

# Alekhya Tumee
###### My favourite place in the world is Hyderabad.

I was born and brought up in Hyderabad which known as **City of Pearls** it is also known as **City of Biryani**. Charminar is a famous monument in hyderabad .I love the vibes that charminar gives me, whenever i was stressed out i used to roam the streets of charminar. It made me forget all my stress and Hyderabad biryani is incomparable, no other city's biryani is as tasty as Hyderabad Biryani.Hyderabad is very beautiful and magical and that's the reason why i love my place hyderabad.

---

### Directions for Travelling from Maryville to Hyderabad
1. The travel time from Maryville to Hyderabad is approximately a day and half.
    1. Take a cab from Maryville to Kansas(MCI) airport. 
    2. from there, take a flight to Chicago. 
    3. from Chicago, take a flight to Delhi.
    4. from Delhi, take a flight to Hyderabad(Destination).
2. items that should be brought to hyderabad for maximum enjoyment.
    * Indian currency.
    * Sunscreen (if you plan to go in summer).
    * Snacks
    * Comfotable clothes
    * Portable charger
    * Earphones
    * Laptop & mobile

[AboutMe](AboutMe.md)

---

### Foods to try in Hyderabad
 | Item | Location | Price|
 |:-----|----------|-----:|
 | Chicken Biryani |Bawarchi,RTC X Roads | $3.5 |
 | Chaat |Gokul Chat,Koti| $0.67 |
 | Irani chai | Nimrah cafe,Charminar | $0.15 |
 | Dosa | Ram-ki-bandi,Abids | $1.3 |

---

>"We are all in the gutter, but some of us are looking at the stars."-- *Oscar Wilde*

>"Knowledge is Power,Knowledge shared is power multiplied."-- *Robert Boyce*

---

### Data structures - Sparse table Algorithm

> Sparse table concept is used for fast queries on a set of static data (elements do not change). It does preprocessing so that the queries can be answered efficiently.
> For more details go to: <https://www.geeksforgeeks.org/sparse-table/> .
```
For Range Sum Queries:-

long long st[MAXN][K + 1];

for (int i = 0; i < N; i++)
    st[i][0] = array[i];

for (int j = 1; j <= K; j++)
    for (int i = 0; i + (1 << j) <= N; i++)
        st[i][j] = st[i][j-1] + st[i + (1 << (j - 1))][j - 1];

 long long sum = 0;
for (int j = K; j >= 0; j--) {
    if ((1 << j) <= R - L + 1) {
        sum += st[L][j];
        L += 1 << j;
    }
}       

For Range Minimum Queries:-

int log[MAXN+1];
log[1] = 0;
for (int i = 2; i <= MAXN; i++)
    log[i] = log[i/2] + 1;

int st[MAXN][K + 1];

for (int i = 0; i < N; i++)
    st[i][0] = array[i];

for (int j = 1; j <= K; j++)
    for (int i = 0; i + (1 << j) <= N; i++)
        st[i][j] = min(st[i][j-1], st[i + (1 << (j - 1))][j - 1]);

int j = log[R - L + 1];
int minimum = min(st[L][j], st[R - (1 << j) + 1][j]);
```