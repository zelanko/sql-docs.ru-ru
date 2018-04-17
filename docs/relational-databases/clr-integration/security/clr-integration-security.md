---
title: Безопасность интеграции со средой CLR | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
caps.latest.revision: 55
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bcf484ba9d27cf430797271ae157b120d41ba7ad
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="clr-integration-security"></a>Безопасность интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Модель безопасности для интеграции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] со средой [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] CLR позволяет управлять доступом и обеспечивать безопасность этого доступа для различных типов объектов (как CLR, так и не CLR), выполняемых в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Для вызова этих объектов может применяться инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] или другой объект CLR, выполняемый на сервере. Вызовы между этими объектами называются связями. Тип проверки безопасности, которая выполняется на этих объектах, зависит от типа связи.  
  
 Модель безопасности для интеграции со средой CLR решает следующие задачи.  
  
-   По умолчанию выполнение управляемого пользовательского кода в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не должно угрожать целостности и стабильности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Выполнение операций, потенциально небезопасных для устойчивости [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], должно быть защищено соответствующими разрешениями высокого уровня.  
  
-   Управляемый пользовательский код не должен получать несанкционированный доступ к пользовательским данным или коду других пользователей в базе данных. Пользовательский программный код должен выполняться в контексте безопасности пользовательского сеанса, который его вызывает, и обладать нужными правами для этого контекста безопасности.  
  
-   Должны существовать элементы управления, ограничивающие доступ пользовательского кода к любым ресурсам за пределами сервера. Он должен использоваться только для доступа к местным данным и для вычислений.  
  
-   Пользовательский программный код не должен получать несанкционированный доступ к системным ресурсам только потому, что он выполняется в процессе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Теперь [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] интегрирует модель безопасности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], контролирующую доступ пользователя, с моделью безопасности CLR, контролирующей доступ кода. В этом разделе обсуждаются некоторые преимущества такого интегрированного подхода.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Безопасность доступом для кода на основе интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
 Обсуждается модель безопасности для управляемого кода, основанная на управлении доступом для кода (CAS).  
  
 [Атрибуты защиты узла и программирование интеграции со средой CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 Содержит сведения о значениях атрибутов защиты узла (host protection attribute, HPA), запрещенных в сборках SAFE и EXTERNAL_ACCESS.  
  
 [Ссылки в средствах безопасности интеграции со средой CLR](http://msdn.microsoft.com/library/168efd01-d12e-4bdf-a1b3-0b5c76474eaf)  
 Описывает механизм вызова фрагментов пользовательского кода друг из друга в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Олицетворение и безопасность интеграции со средой CLR](http://msdn.microsoft.com/library/1495a7af-2248-4cee-afdb-9269fb3a7774)  
 Описывает доступ управляемого кода к внешним ресурсам с использованием олицетворения.  
  
 [Частично доверенный вызывающий код](http://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
 Описывает проблемы, возникающие, когда управляемый метод вызывает метод класса, содержащегося в другой сборке.  
  
 [Домены приложений и безопасность интеграции со средой CLR](http://msdn.microsoft.com/library/54ee904e-e21a-4ee7-b4ad-a6f6f71bd473)  
 Описывает загрузку сборок в домены приложений.  
  
## <a name="see-also"></a>См. также  
 [Управление сборками интеграции со средой CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)  
  
  
