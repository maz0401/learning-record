# Java 集合相关问题文档

## 集合转换问题

### 1、Collection转换List\Array

```
public void testMap2List() throws Exception{
    Map<String, String> map = new HashMap<String, String>();
    map.put("1", "AA");
    map.put("2", "BB");
    map.put("3", "CC");
    
    // get collection
    Collection<String> valueCollection = map.values();
    final int size = valueCollection.size();
   
    // Collection to List
    List<String> valueList = new ArrayList<String>(valueCollection);

    // Collection to Array
    String[] valueArray = new String[size];
    map.values().toArray(valueArray);
}
```