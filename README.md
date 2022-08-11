# -changed-value
# It starts at the (0, 0) position in the coordinate plane. The boundary of the coordinate plane consists of upper left (-5, 5), lower left (-5, -5), upper right (5, 5), and lower right (5, -5). Save the street! 좌표평면의 (0, 0) 위치에서 시작합니다. 좌표평면의 경계는 왼쪽 위(-5, 5), 왼쪽 아래(-5, -5), 오른쪽 위(5, 5), 오른쪽 아래(5, -5)로 이루어져 있고 이범위 사이에서 캐릭터가 움직이는 거리를 구해라!
# c program
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
int area[11][11][4]; //[4]=위,아래,오른,왼
int solution(const char* dirs) {
    int x=5,y=5,m; //증가되는 값
    int x1=5,y1=5,m1; //처음 값
    int n=0;
    int i;
    for(i=0;dirs[i]!='\0';i++){
    char s=dirs[i];
    if(s=='U'&&y<10){
    y++;
    m=1;
    m1=0;}
    else if(s=='D'&&y>0){
    y--;
    m=0;
    m1=1;
    }
    else if(s=='R'&&x<10){
    x++;
    m=3;
    m1=2;
    }
    else if(s=='L'&&x>0){
    x--;
    m=2;
    m1=3;
    }
    else{
    continue;
    }
    if(area[y1][x1][m1]==0){
    area[y1][x1][m1]=1;
    area[y][x][m]=1;
    n++;
    }
    x1=x;
    y1=y;
    }
    return n;
}
int main(void){
    char dirs='LULLLLLLU';
    solution(dirs);
    return 0;
}
# python
def solution(dirs):
    a=set()
    dic={'U':(0,1),'D':(0.-1),'R':(1,0),'L':(-1,0)}
    x,y=0,0
    s=0
    for i in dirs:
        nx,ny=x+dic[i][0],y+dic[i][1] #nx와 ny는 처음부터 증가하는 부분의 길이
        if -5<=nx<=5 and -5<=ny<=5:
            a.add((x,y,nx,ny))
            a.add((nx,ny,x,y))
            x,y=nx,ny
    return len(a)//2
dirs='L','U','L','L','L','L','L','L','U'
print(solution(dirs))
#result--> 7
