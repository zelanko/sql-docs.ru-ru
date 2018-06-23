---
title: Настраиваемые атрибуты для процедур CLR значением | Документы Microsoft
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
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
caps.latest.revision: 82
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 21bb0d5bd6ea5dfe672b47ee9095416da6267dbf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098206"
---
# <a name="custom-attributes-for-clr-routines"></a>Пользовательские атрибуты для процедур CLR
  Перечисленные атрибуты могут применяться для общих подпрограмм языка среды CLR, определяемые пользователем типы и определяемые пользователем статистические функции, которые зарегистрированы в [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]. Если атрибут не применен, то [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предполагает значение по умолчанию. Перечисленные атрибуты определены в пространстве имен `Microsoft.SqlServer.Server`.  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Атрибут SqlUserDefinedAggregate  
 Атрибут `SqlUserDefinedAggregate` указывает, что метод должен быть зарегистрирован как пользовательское статистическое выражение. Каждое пользовательское статистическое выражение должно иметь этот атрибут.  
  
 Дополнительные сведения см. в разделе [SqlUserDefinedAggregateAttribute](http://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="the-sqlfunction-attribute"></a>Атрибут SqlFunction  
 Атрибут `SqlFunction` указывает, что метод должен быть зарегистрирован как функция, с соответствующим функции набором атрибутов.  
  
 Дополнительные сведения см. в разделе [SqlFunctionAttribute](http://go.microsoft.com/fwlink/?LinkId=128019).  
  
## <a name="the-sqlfacet-attribute"></a>Атрибут SqlFacet  
 Атрибут `SqlFacet` позволяет получить сведения о возвращаемом типе выражения определяемого пользователем типа данных.  
  
 Дополнительные сведения см. в разделе [SqlFacetAttribute](http://go.microsoft.com/fwlink/?LinkId=128020).  
  
## <a name="the-sqlprocedure-attribute"></a>Атрибут SqlProcedure  
 Атрибут `SqlProcedure` указывает, что метод должен быть зарегистрирован как хранимая процедура. Этот атрибут используется только в среде Visual Studio для автоматической регистрации указанного метода как хранимой процедуры. В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не используется.  
  
 Дополнительные сведения см. в разделе [SqlProcedureAttribute](http://go.microsoft.com/fwlink/?LinkId=128021).  
  
## <a name="the-sqltrigger-attribute"></a>Атрибут SqlTrigger  
 Атрибут `SqlTrigger` указывает, что метод должен быть зарегистрирован как триггер.  
  
 Дополнительные сведения см. в разделе [SqlTriggerContext](http://go.microsoft.com/fwlink/?LinkId=128022) и [SqlTriggerAttribute](http://go.microsoft.com/fwlink/?LinkId=203898).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 К определению класса в сборке можно применить SqlUserDefinedTypeAttribute. В результате этого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] создает определяемый пользователем тип, привязанный к определению класса с этим пользовательским атрибутом.  
  
 Дополнительные сведения см. в разделе [SqlUserDefinedTypeAttribute](http://go.microsoft.com/fwlink/?LinkId=128024).  
  
## <a name="the-sqlmethod-attribute"></a>Атрибут SqlMethod  
 Атрибут `SqlMethod` позволяет определить детерминированность и свойства доступа к данным метода или свойства определяемого пользователем типа.  
  
 Дополнительные сведения см. в разделе [SqlMethodAttribute](http://go.microsoft.com/fwlink/?LinkId=128025).  
  
## <a name="see-also"></a>См. также  
 [Определяемые пользователем статистические функции CLR](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Определяемые пользователем функции среды CLR](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Определяемые пользователем типы среды CLR](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Хранимые процедуры CLR](../../../database-engine/dev-guide/clr-stored-procedures.md)   
 [Триггеры CLR](../../../database-engine/dev-guide/clr-triggers.md)  
  
  