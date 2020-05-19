---
title: Объект Склксмладаптер (управляемые классы SQLXML) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 86231096c8eef084b36d6195a1c720bd4f9038a3
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717957"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>Объект SqlXmlAdapter (управляемые классы SQLXML)
  В этом объекте реализованы методы, облегчающие взаимодействие с набором данных в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Рабочий пример см. в разделе [доступ к функциям SQLXML в среде .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Объект Склксмладаптер поддерживает следующие методы:  
  
 void Fill (набор данных DS)  
 Заполняет набор данных в .NET Framework XML-данными, полученными от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 пустое обновление (набор данных DS)  
 Применяет обновления к записям в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из данных, содержащихся в наборе данных.  
  
 Объект Склксмладаптер поддерживает следующие конструкторы:  
  
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
  
  
