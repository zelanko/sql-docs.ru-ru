---
description: Преобразования XSLT
title: Преобразования XSLT | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XSLT transformations in ADO
ms.assetid: 1a46196e-839f-4734-a59e-2c64609ffb9e
author: rothja
ms.author: jroth
ms.openlocfilehash: a704245d166b0d53cb7ed17e6a5f8cdfa32d9447
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978805"
---
# <a name="xslt-transformations"></a>Преобразования XSLT
XSLT можно применить к созданному XML-документу, чтобы преобразовать его в другой формат. Понимание формата XML в ADO помогает в разработке шаблонов XSLT, которые могут преобразовать его в более понятную для пользователя форму.  
  
 Например, известно, что каждая строка набора записей сохраняется как элемент з:ров внутри элемента RS: Data. Аналогичным образом каждое поле набора записей сохраняется как пара "атрибут-значение" для этого элемента.  
  
## <a name="remarks"></a>Remarks  
 Следующий скрипт XSLT можно применить к XML-данным, приведенным в предыдущем разделе, чтобы преобразовать его в HTML-таблицу для отображения в браузере:  
  
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
  
 XSLT преобразует XML-поток, созданный методом сохранения ADO, в таблицу HTML, которая отображает каждое поле набора записей вместе с заголовком таблицы. Заголовкам и строкам таблиц также присваиваются различные шрифты и цвета.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](./persisting-records-in-xml-format.md)