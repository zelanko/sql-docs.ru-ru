---
title: Преобразования XSLT | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XSLT transformations in ADO
ms.assetid: 1a46196e-839f-4734-a59e-2c64609ffb9e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59b00a521624759af8f73a94f75c4a74101b1937
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47839682"
---
# <a name="xslt-transformations"></a>Преобразования XSLT
XSLT могут применяться в созданный XML-документ для преобразования его в другой формат. Общие сведения о формате XML в ADO помогает в разработке XSLT-шаблоны, которые можно преобразовать в более удобные форму.  
  
 Например вы знаете, что каждой строки набора записей сохраняется как элемент z: строки внутри rs: данные элемента. Аналогичным образом каждое поле в наборе записей сохраняется как пара "атрибут значение" для данного элемента.  
  
## <a name="remarks"></a>Примечания  
 Следующий скрипт XSLT могут применяться к XML, показанный в предыдущем разделе, преобразовать его в таблицу HTML для отображения в браузере:  
  
```  
<?xml version="1.0" encoding="ISO-8859-1"?>  
<html xmlns:xsl="http://www.w3.org/TR/WD-xsl">  
<body STYLE="font-family:Arial, helvetica, sans-serif; font-size:12pt; background-color:white">  
<table border="1" style="table-layout:fixed" width="600">  
  <col width="200"></col>  
  <tr bgcolor="teal">  
    <th><font color="white">CustomerId</font></th>  
    <th><font color="white">CompanyName</font></th>  
    <th><font color="white">ContactName</font></th>  
  </tr>  
<xsl:for-each select="xml/rs:data/z:row">  
  <tr bgcolor="navy">  
    <td><font color="white"><xsl:value-of select="@CustomerID"/></font></td>  
    <td><font color="white"><xsl:value-of select="@CompanyName"/></font></td>  
    <td><font color="white"><xsl:value-of select="@ContactName"/></font></td>   
  </tr>  
</xsl:for-each>  
</table>  
</body>  
</html>  
```  
  
 XSLT преобразует потоком XML, созданным с помощью метода ADO сохранить в таблицу HTML, в котором отображаются все поля в наборе записей, а также заголовок таблицы. Заголовки таблицы и строки также назначаются различные шрифты и цвета.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
