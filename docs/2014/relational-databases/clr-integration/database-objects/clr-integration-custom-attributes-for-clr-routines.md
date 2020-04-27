---
title: Пользовательские атрибуты подпрограмм среды CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 817591cec64a4210c4cc573588be1b8ac6dfb8a7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62873806"
---
# <a name="custom-attributes-for-clr-routines"></a>Пользовательские атрибуты для процедур CLR
  Перечисленные атрибуты можно применять к подсредам среды CLR, определяемым пользователем типам и определяемым пользователем статистическим функциям, зарегистрированным в [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]. Если атрибут не применен, то [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предполагает значение по умолчанию. Перечисленные атрибуты определены в пространстве имен `Microsoft.SqlServer.Server`.  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Атрибут SqlUserDefinedAggregate  
 Атрибут `SqlUserDefinedAggregate` указывает, что метод должен быть зарегистрирован как пользовательское статистическое выражение. Каждое пользовательское статистическое выражение должно иметь этот атрибут.  
  
 Дополнительные сведения см. в разделе [склусердефинедаггрегатеаттрибуте](https://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="the-sqlfunction-attribute"></a>Атрибут SqlFunction  
 Атрибут `SqlFunction` указывает, что метод должен быть зарегистрирован как функция, с соответствующим функции набором атрибутов.  
  
 Дополнительные сведения см. в разделе [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019).  
  
## <a name="the-sqlfacet-attribute"></a>Атрибут SqlFacet  
 Атрибут `SqlFacet` позволяет получить сведения о возвращаемом типе выражения определяемого пользователем типа данных.  
  
 Дополнительные сведения см. в разделе [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020).  
  
## <a name="the-sqlprocedure-attribute"></a>Атрибут SqlProcedure  
 Атрибут `SqlProcedure` указывает, что метод должен быть зарегистрирован как хранимая процедура. Этот атрибут используется только в среде Visual Studio для автоматической регистрации указанного метода как хранимой процедуры. В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не используется.  
  
 Дополнительные сведения см. в разделе [склпроцедуреаттрибуте](https://go.microsoft.com/fwlink/?LinkId=128021).  
  
## <a name="the-sqltrigger-attribute"></a>Атрибут SqlTrigger  
 Атрибут `SqlTrigger` указывает, что метод должен быть зарегистрирован как триггер.  
  
 Дополнительные сведения см. в разделе [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) и [склтригжераттрибуте](https://go.microsoft.com/fwlink/?LinkId=203898).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 К определению класса в сборке можно применить SqlUserDefinedTypeAttribute. В результате этого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] создает определяемый пользователем тип, привязанный к определению класса с этим пользовательским атрибутом.  
  
 Дополнительные сведения см. в разделе [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024).  
  
## <a name="the-sqlmethod-attribute"></a>Атрибут SqlMethod  
 Атрибут `SqlMethod` позволяет определить детерминированность и свойства доступа к данным метода или свойства определяемого пользователем типа.  
  
 Дополнительные сведения см. в разделе [склмесодаттрибуте](https://go.microsoft.com/fwlink/?LinkId=128025).  
  
## <a name="see-also"></a>См. также  
 [Определяемые пользователем статистические функции CLR](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Определяемые пользователем функции среды CLR](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Определяемые пользователем типы данных CLR](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Хранимые процедуры CLR](../../../database-engine/dev-guide/clr-stored-procedures.md)   
 [Триггеры CLR](../../../database-engine/dev-guide/clr-triggers.md)  
  
  
