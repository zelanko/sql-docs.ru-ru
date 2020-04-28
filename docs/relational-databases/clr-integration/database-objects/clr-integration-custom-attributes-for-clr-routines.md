---
title: Пользовательские атрибуты подпрограмм среды CLR | Документация Майкрософт
description: Настраиваемые атрибуты можно применять к подсредам CLR, определяемым пользователем типам и определяемым пользователем статистическим функциям, зарегистрированным в Microsoft SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: a32a606f73858ede15569d1ade891ad2ce1c69a5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81487973"
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>Пользовательские атрибуты интеграции со средой CLR для процедур CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Перечисленные атрибуты можно применять к подсредам среды CLR, определяемым пользователем типам и определяемым пользователем статистическим функциям, зарегистрированным в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если атрибут не применен, то [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предполагает значение по умолчанию. Перечисленные атрибуты определены в пространстве имен **Microsoft. SqlServer. Server** .  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Атрибут SqlUserDefinedAggregate  
 Атрибут **SqlUserDefinedAggregate** указывает, что метод должен быть зарегистрирован как определяемая пользователем статистическая функция. Каждое пользовательское статистическое выражение должно иметь этот атрибут.  
  
 Дополнительные сведения см. в разделе [склусердефинедаггрегатеаттрибуте](https://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="the-sqlfunction-attribute"></a>Атрибут SqlFunction  
 Атрибут **SqlFunction** указывает, что метод должен быть зарегистрирован как функция с указанием соответствующих атрибутов функции.  
  
 Дополнительные сведения см. в разделе [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019).  
  
## <a name="the-sqlfacet-attribute"></a>Атрибут SqlFacet  
 Атрибут **склфацет** используется для получения сведений о типе возвращаемого значения выражения определяемого пользователем типа (UDT).  
  
 Дополнительные сведения см. в разделе [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020).  
  
## <a name="the-sqlprocedure-attribute"></a>Атрибут SqlProcedure  
 Атрибут **склпроцедуре** указывает, что метод должен быть зарегистрирован в качестве хранимой процедуры. Этот атрибут используется только в среде Visual Studio для автоматической регистрации указанного метода как хранимой процедуры. В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не используется.  
  
 Дополнительные сведения см. в разделе [склпроцедуреаттрибуте](https://go.microsoft.com/fwlink/?LinkId=128021).  
  
## <a name="the-sqltrigger-attribute"></a>Атрибут SqlTrigger  
 Атрибут **склтригжер** указывает, что метод должен быть зарегистрирован в качестве триггера.  
  
 Дополнительные сведения см. в разделе [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) и [склтригжераттрибуте](https://go.microsoft.com/fwlink/?LinkId=203898).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 К определению класса в сборке можно применить SqlUserDefinedTypeAttribute. В результате этого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] создает определяемый пользователем тип, привязанный к определению класса с этим пользовательским атрибутом.  
  
 Дополнительные сведения см. в разделе [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024).  
  
## <a name="the-sqlmethod-attribute"></a>Атрибут SqlMethod  
 Атрибут **склмесод** используется для указания свойств детерминированности и доступа к данным метода или свойства определяемого пользователем типа.  
  
 Дополнительные сведения см. в разделе [склмесодаттрибуте](https://go.microsoft.com/fwlink/?LinkId=128025).  
  
## <a name="see-also"></a>См. также:  
 [Определяемые пользователем статистические функции CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Определяемые пользователем функции среды CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Определяемые пользователем типы данных CLR](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Хранимые процедуры CLR](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [Триггеры CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  
