#### 打印在数组中出现n/2以上次数的元素

思路：利用HashMap存储数组元素，value值按数组内元素出现次数填入，key值便存储相应的数组元素。

```
public Class HashMapTest{
  public void main(String [] args){
     int[] a={2,2,2,2,1,4,2,2,2,7,9,6,2,2,3,1,0};
      Map<Integer,Integer>map=new HashMap<Integer,Integer>(); 
      for(int i=0;i<a.length;i++){
        if(map.containKey(a[i])){
         int tmp=map.get(a[i]);
          tmp+=1;
          map.put(a[i],tmp);//多次出现的元素
       }else{
          map.put(a[i],1); //只出现一次的元素
      } 
    }
    Set<Integet>set=map.keySet();
    for(Integer s:set){
     if(map.get(s)>a.length/2){  //根据key值来获取value值也就是对应的元素的出现次数
     System,out.println(s);  
     }  
   }
}
```:wq

