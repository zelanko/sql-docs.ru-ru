---
title: "Преобразования XSLT | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XSLT transformations in ADO
ms.assetid: 1a46196e-839f-4734-a59e-2c64609ffb9e
caps.latest.revision: "3"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7fb8a2fc948c7793ed07076f338c230350d6abb1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="xslt-transformations"></a>Преобразования XSLT
Преобразования XSLT можно применять к созданным XML, преобразовать его в другой формат. Основные сведения о формате XML в ADO помогает в разработке XSLT-шаблонов, которые можно преобразовать его в форме более удобной для пользователей.  
  
 Например вы знаете, что каждой строки набора записей сохраняется как элемент z: строк внутри элемента rs: данные. Аналогичным образом каждое поле Recordset сохраняется как пары атрибут значение для этого элемента.  
  
## <a name="remarks"></a>Замечания  
 Следующий скрипт XSLT может применяться к код XML, показанный в предыдущем разделе преобразовать его в HTML-таблицы для отображения в браузере:  
  
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
  
 XSLT преобразует XML-потока, созданного методом ADO сохранить в таблицу HTML, в котором отображаются все поля набора записей, а также заголовок таблицы. Заголовки таблицы и строки также назначаются различные шрифты и цвета.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
