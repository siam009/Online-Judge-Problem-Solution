#include<bits/stdc++.h>
using namespace std;

#define ll unsigned long long int

int main()
{
    int n=16;
    string s[18];
    for(int i=1; i<=n; i++)
        cin>>s[i];
    int a[n+2][n+2];
    for(int i=1; i<=n; i++)
    {
        for(int j=1; j<=n; j++)
        {
            cin>>a[i][j];
        }
    }
    double ans[17][5];
    for(int i=1; i<=16; i++)
    {
        if(i%2)
            ans[i][1]=1.0*a[i][i+1]/100.0;
        else
            ans[i][1]=1.0*a[i][i-1]/100.0;
    }
    for(int i=1; i<=16; i+=4)
    {
        ans[i][2]=ans[i][1]*(ans[i+2][1]*a[i][i+2]/100.0+ans[i+3][1]*a[i][i+3]/100.0);
        ans[i+2][2]=ans[i+2][1]*(ans[i][1]*a[i+2][i]/100.0+ans[i+1][1]*a[i+2][i+1]/100.0);
        ans[i+3][2]=ans[i+3][1]*(ans[i][1]*a[i+3][i]/100.0+ans[i+1][1]*a[i+3][i+1]/100.0);
        ans[i+1][2]=ans[i+1][1]*(ans[i+2][1]*a[i+1][i+2]/100.0+ans[i+3][1]*a[i+1][i+3]/100.0);
    }
    for(int i=1;i<=16;i+=8)
    {
        ans[i][3]=ans[i][2]*(ans[i+4][2]*a[i][i+4]/100.0+ans[i+5][2]*a[i][i+5]/100.0+ans[i+6][2]*a[i][i+6]/100.0+ans[i+7][2]*a[i][i+7]/100.0);
        ans[i+1][3]=ans[i+1][2]*(ans[i+4][2]*a[i+1][i+4]/100.0+ans[i+5][2]*a[i+1][i+5]/100.0+ans[i+6][2]*a[i+1][i+6]/100.0+ans[i+7][2]*a[i+1][i+7]/100.0);
        ans[i+2][3]=ans[i+2][2]*(ans[i+4][2]*a[i+2][i+4]/100.0+ans[i+5][2]*a[i+2][i+5]/100.0+ans[i+6][2]*a[i+2][i+6]/100.0+ans[i+7][2]*a[i+2][i+7]/100.0);
        ans[i+3][3]=ans[i+3][2]*(ans[i+4][2]*a[i+3][i+4]/100.0+ans[i+5][2]*a[i+3][i+5]/100.0+ans[i+6][2]*a[i+3][i+6]/100.0+ans[i+7][2]*a[i+3][i+7]/100.0);
        ans[i+4][3]=ans[i+4][2]*(ans[i][2]*a[i+4][i]/100.0+ans[i+1][2]*a[i+4][i+1]/100.0+ans[i+2][2]*a[i+4][i+2]/100.0+ans[i+3][2]*a[i+4][i+3]/100.0);
        ans[i+5][3]=ans[i+5][2]*(ans[i][2]*a[i+5][i]/100.0+ans[i+1][2]*a[i+5][i+1]/100.0+ans[i+2][2]*a[i+5][i+2]/100.0+ans[i+3][2]*a[i+5][i+3]/100.0);
        ans[i+6][3]=ans[i+6][2]*(ans[i][2]*a[i+6][i]/100.0+ans[i+1][2]*a[i+6][i+1]/100.0+ans[i+2][2]*a[i+6][i+2]/100.0+ans[i+3][2]*a[i+6][i+3]/100.0);
        ans[i+7][3]=ans[i+7][2]*(ans[i][2]*a[i+7][i]/100.0+ans[i+1][2]*a[i+7][i+1]/100.0+ans[i+2][2]*a[i+7][i+2]/100.0+ans[i+3][2]*a[i+7][i+3]/100.0);
    }
    for(int i=1;i<=8;i++)
    {
        double temp=0.0;
        for(int j=9;j<=16;j++)
        {
            temp+=(ans[j][3]*a[i][j]/100.0);
        }
        ans[i][4]=ans[i][3]*temp*100.0;
    }
    for(int i=9;i<=16;i++)
    {
        double temp=0.0;
        for(int j=1;j<=8;j++)
        {
            temp+=(ans[j][3]*a[i][j]/100.0);
        }
        ans[i][4]=ans[i][3]*temp*100.0;
    }
    for(int i=1;i<=16;i++)
    {
        cout<<s[i];
        for(int j=s[i].size();j<11;j++)
            cout<<" ";
        cout<<"p="<<fixed<<setprecision(2)<<ans[i][4]<<"%"<<endl;
    }
    return 0;
}
