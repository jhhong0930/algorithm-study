# algorithm-study
각자 이름으로 브렌치 만드신 후 해당 주차 스터디 진행 전까지 푸시 하시면 됩니다  

### 1주차 문제
- 로또의 최고 순위와 최저 순위 https://programmers.co.kr/learn/courses/30/lessons/77484
- 신규 아이디 추천 https://programmers.co.kr/learn/courses/30/lessons/72410
- 숫자 문자열과 영단어 https://programmers.co.kr/learn/courses/30/lessons/81301
- 키패드 누르기 https://programmers.co.kr/learn/courses/30/lessons/67256
- 크레인 인형뽑기 게임 https://programmers.co.kr/learn/courses/30/lessons/64061



현솔

로또

로또의 최고순위와 최저순위 (20분소요)

class Solution {
    public int[] solution(int[] lottos, int[] win_nums) {
       
        
        int b = min(lottos,win_nums);
        int a = max(lottos,win_nums);
        
        int[] answer = {a,b};
    
        return answer;
    }
    
    public int max(int[] lottos, int[] win_nums){
        int result=0;
        int count=0;
        for(int i=0; i<lottos.length; i++){
           
            for(int f=0; f<win_nums.length; f++){
               
                 if(lottos[i]==0){
                    lottos[i]=win_nums[i];                
                 }
                
                if(lottos[i]==win_nums[f]){
                    count+=1;
                }
            }
        }
       switch(count){
             
           case 6: result=1; break;
           case 5: result=2; break;
           case 4: result=3; break;    
           case 3: result=4; break;    
           case 2: result=5; break;
           default: result=6; break;    
       }
        return result; 
    }
    
 public int min(int[] lottos, int[] win_nums){
          int result=0;
          int count=0;
          for(int i=0; i<lottos.length; i++){
           
            for(int f=0; f<win_nums.length; f++){
                
                if(lottos[i]==win_nums[f]){
                    count+=1;
                }
            }
          }
       switch(count){
             
           case 6: result=1; break;
           case 5: result=2; break;
           case 4: result=3; break;    
           case 3: result=4; break;    
           case 2: result=5; break;
           default: result=6; break;    
       }
        return result; 
        
    }
    
}


키패드 누르기 (1시간 반소요)

class Solution {
    public String solution(int[] numbers, String hand) {
        
        int[] rightF ={3,2} ; //오른손 현재위치
        int[] leftF = {3,0}; //왼손 현재위치              
        String answer = "";      
               
        int distantL=0;
        int distantR=0;
            
         //1,2,3,4,5,6,7,8,9,*,0,#
        int[][] pad = {{1,2,3},
                       {4,5,6},
                       {7,8,9},
                       {10,0,12}};  
        
           
              for(int n=0; n<numbers.length; n++){
                 for(int i=0; i<pad.length; i++){
                     for(int j=0; j<pad[i].length; j++){
                    
                         if(numbers[n]==pad[i][j]){
                             
                             if(numbers[n]%3==1){
                                 leftF[0]=i;
                                 leftF[1]=j;
                                 answer+="L";
                                 
                             }  else if(numbers[n]%3==0 && numbers[n]!=0){
                                 
                                 rightF[0]=i;
                                 rightF[1]=j;
                                 answer+="R";
                                 
                             }  else {
                                distantL= Math.abs(leftF[0]-i)+Math.abs(leftF[1]-j);
                                distantR= Math.abs(rightF[0]-i)+Math.abs(rightF[1]-j);
                                 
                                 if(distantL<distantR){
                                      leftF[0]=i;
                                     leftF[1]=j;
                                     answer+="L";
                                 } else  if(distantL>distantR){
                                      rightF[0]=i;
                                      rightF[1]=j;
                                      answer+="R";
                                 } else {
                                     if(hand.equals("right")){
                                      rightF[0]=i;
                                      rightF[1]=j;
                                      answer+="R";
                                     } else{
                                           leftF[0]=i;
                                     leftF[1]=j;
                                     answer+="L";
                                     }
                                 }
                                 
                                 
                             }                       
                             
                             
                         }
                         
                       }    
                    }      
                }
         
       
        return answer;
    }
}

