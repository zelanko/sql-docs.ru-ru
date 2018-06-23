---
title: Объект SqlXmlAdapter (управляемые классы SQLXML) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d657ba49f7d4905eef8eaa0bdc3ca4327852df6d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190368"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>Объект SqlXmlAdapter (управляемые классы SQLXML)
  В этом объекте реализованы методы, облегчающие взаимодействие с набором данных в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Работающий пример см. в разделе [доступ к функциональным возможностям SQLXML в среде .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Объект SqlXmlAdapter поддерживает следующие методы:  
  
 void Fill (DataSet ds)  
 Заполняет набор данных в .NET Framework XML-данными, полученными от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 void Update (DataSet ds)  
 Применяет обновления к записям в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из данных, содержащихся в наборе данных.  
  
 Объект SqlXmlAdapter поддерживает следующие конструкторы:  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>См. также  
 [Объект SqlXmlCommand &#40;управляемые классы SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)   
 [Объект SqlXmlParameter &#40;управляемые классы SQLXML&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  