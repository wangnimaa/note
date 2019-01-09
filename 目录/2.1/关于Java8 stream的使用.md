Java的stream提供了非常方便的数据处理api。

list.stream().collect(Collectors.groupingBy(DTO::getName));  根据name字段进行分组，分组后的顺序和之前的不一致。如果想一致，建议使用LinkedHashMap,如下：

list.stream().collect(Collectors.groupingBy(DTO::getName, LinkedHashMap::new,Collectors.toList()));

list.stream().sorted(Comparator.comparing(DTO::getName)).collect(Collectors.toList()) 根据name字段排序，升序，插入排序。如果想获得相反顺序，使用reversed的方法。

