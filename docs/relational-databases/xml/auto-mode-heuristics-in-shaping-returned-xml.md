---
title: Эвристические методы режима AUTO, используемые при формировании возвращаемого XML-кода | Документация Майкрософт
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||=azuresqldb-mi-current||>=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions
ms.openlocfilehash: 408589a38ae9b01777110bbab1fb3b20c380a6c6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68029339"
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a>Эвристические методы режима AUTO, используемые при формировании возвращаемого XML-кода

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Режим AUTO определяет основанную на запросе структуру возвращаемого XML. При определении схемы вложения элементов применяемые в режиме AUTO эвристические процедуры сравнивают значения столбцов в соседних строках. Сравниваются столбцы всех типов, за исключением **ntext**, **text**, **image**и **xml**. Проводится также сравнение столбцов **(n)varchar(max)** и **varbinary(max)** .  
  
 В следующем примере иллюстрируются эвристики режима AUTO, определяющие структуру результирующего XML:  
  
```sql
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
ORDER BY T1.Id
FOR XML AUTO;
```  
  
 Для определения начала нового элемента <`T1`> сравниваются все значения столбцов таблицы T1, за исключением столбцов типов данных **ntext**, **text**, **image** и **xml**, если ключ таблицы Т1 не задан. Далее предположим, что столбец **Name** имеет тип данных **nvarchar(40)** и инструкция SELECT возвращает следующий набор строк:  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 Эвристики режима AUTO сравнивают все значения столбцов Id и Name таблицы Т1. Так как первые две строки имеют одинаковые значения столбцов Id и Name, в результат добавляется один элемент \<T1>, имеющий два дочерних элемента \<T2>.  
  
 Далее показан возвращенный XML:  
  
```xml
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 Теперь предположим, что столбец Name имеет тип данных **text** . Эвристики режима AUTO не выполняют сравнения для этого типа. Вместо этого в них предполагается, что значения различны. Это приводит к формированию приведенного ниже XML:  
  
```xml
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование AUTO Mode с FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)  
  
  
