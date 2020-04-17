---
title: Пользовательские атрибуты для CLR Рутины (ru) Документы Майкрософт
description: Пользовательские атрибуты могут быть применены к процедурам CLR, типам, определенным пользователям, и пользовательским агрегатам, зарегистрированным на сервере Microsoft S'L.
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487973"
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>Пользовательские атрибуты интеграции со средой CLR для процедур CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Перечисленные атрибуты могут быть применены к общим языковым процедурам выполнения (CLR), определенным типам [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]пользователей и пользовательским агрегатам, зарегистрированным в. Если атрибут не применен, то [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предполагает значение по умолчанию. Перечисленные атрибуты определены в пространстве имен **Microsoft.SqlServer.Server.**  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Атрибут SqlUserDefinedAggregate  
 Атрибут **SqlUserDefinedAggregate** указывает на то, что метод должен быть зарегистрирован как пользовательский агрегат. Каждое пользовательское статистическое выражение должно иметь этот атрибут.  
  
 Для получения дополнительной информации [см.](https://go.microsoft.com/fwlink/?LinkId=124626)  
  
## <a name="the-sqlfunction-attribute"></a>Атрибут SqlFunction  
 Атрибут **SlFunction** указывает на то, что метод должен быть зарегистрирован как функция с соответствующим набором атрибутов функции.  
  
 Для получения дополнительной информации [см.](https://go.microsoft.com/fwlink/?LinkId=128019)  
  
## <a name="the-sqlfacet-attribute"></a>Атрибут SqlFacet  
 Атрибут **SqlFacet** используется для возврата информации о типе возврата пользовательского типа (UDT).  
  
 Для получения дополнительной информации [см.](https://go.microsoft.com/fwlink/?LinkId=128020)  
  
## <a name="the-sqlprocedure-attribute"></a>Атрибут SqlProcedure  
 Атрибут **SqlProcedure** указывает на то, что метод должен быть зарегистрирован как сохраненная процедура. Этот атрибут используется только в среде Visual Studio для автоматической регистрации указанного метода как хранимой процедуры. В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не используется.  
  
 Для получения дополнительной информации [см.](https://go.microsoft.com/fwlink/?LinkId=128021)  
  
## <a name="the-sqltrigger-attribute"></a>Атрибут SqlTrigger  
 Атрибут **SqlTrigger** указывает на то, что метод должен быть зарегистрирован в качестве триггера.  
  
 Для получения дополнительной информации [SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898)см. [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022)  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 К определению класса в сборке можно применить SqlUserDefinedTypeAttribute. В результате этого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] создает определяемый пользователем тип, привязанный к определению класса с этим пользовательским атрибутом.  
  
 Для получения дополнительной информации [см.](https://go.microsoft.com/fwlink/?LinkId=128024)  
  
## <a name="the-sqlmethod-attribute"></a>Атрибут SqlMethod  
 Атрибут **SqlMethod** используется для обозначения детерминизма и свойств доступа к данным метода или свойства на UDT.  
  
 Для получения дополнительной информации [см.](https://go.microsoft.com/fwlink/?LinkId=128025)  
  
## <a name="see-also"></a>См. также:  
 [ClR Пользовательские агрегаты](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Функции, определяемые пользователем CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Типы, определяемые пользователями CLR](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Процедуры хранения CLR](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [Триггеры CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  
