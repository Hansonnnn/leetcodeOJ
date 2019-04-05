#### roman to integer

罗马数字转换为int数字

Question：数字范围为1~3999，将此范围的罗马数字转换为整形数字
思路：罗马数字有I(1),V(5),X(10),L(50),C(100),D(500),M(1000),7种构成，构成数字方式为：I，II,III,IV,V,VI,VII,VIII,IX,X,XI....表示1到11的整型数字，根据其进位规则，可以设置一个字符串用来存储7个罗马数字，另外初始化一个整型数组来存储其一一对应的整型数字，然后需要做的是循环传入罗马数字中的每一位并在整形数组中取出其代表的数字，具体做法如下：

```
public int romanToInt(String s){
    String roman="IVXLCDM";//罗马数字
    int []num ={1,5,10,50,100,500,1000};
    int preId=roman.indexOf(s.charAt(0));
    int result=num[preId];
    for(int i=1;i<s.length();i++){
        int currId=roman.indexOf(s.charAt(i));
        if(preId<currId){
            result +=num[currId]-2*num[preId];
        }else{
            result +=num[currId];
        }
        preId=currId;
    }
    return  result;

}
