- [Problem's Link](https://www.spoj.com/problems/CANDY3/)
- Solution:





```c
/*#include<stdio.h>
int main()
{
    int t;
    scanf("%d",&t);
    for(int i=0;i<t;i++)
    {
        long long int n;
        scanf("%lld",&n);
        long long int sum=0, s;
        for(int i=0; i<n; i++)
        {
            scanf("%lld",&s);
            sum+=s;
        }
        if(sum%n==0)
        printf("YES");
        else printf("NO");
    }
} 

 gives wrong solution, maybe beacuse the time limit exceeds, but the logic is fine...

when written slightly differently:*/



#include<stdio.h>
int main()
{
    int t;
    scanf("%d",&t);
    while(t--)
    {
        long long int ppl,i,sum=0,temp;
        scanf("%lld",&ppl);
        for(i=0;i<ppl;i++)
        {
            scanf("%lld",&temp);
            sum=(sum+temp)%ppl;
        }
        if(sum)
            printf("NO\n");
        else
            printf("YES\n");
    }
    return 0;
}
```
