---
title: Общие принципы программирования интеграции языка среды выполнения (CLR) | Документы Microsoft
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
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
caps.latest.revision: 56
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3f508cdada9905c2a8ec322319df58cb5504af14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190009"
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a>Основные понятия о программировании интеграции со средой CLR
  Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обеспечивает интеграцию с компонентами CLR платформы .NET Framework для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Это означает, что хранимые процедуры, триггеры, определяемые пользователем типы, определяемые пользователем функции, определяемые пользователем статистические функции и возвращающие табличные значение потоковые функции теперь могут разрабатываться с использованием любого языка .NET Framework, включая [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET и [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.  
  
 Пространство имен Microsoft.SqlServer.Server содержит основные возможности программирования CLR для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Однако пространство имен Microsoft.SqlServer.Server документировано в пакете .NET Framework SDK. Эта документация не включена в электронную документацию по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  По умолчанию платформа .NET Framework устанавливается вместе с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], но пакет .NET Framework SDK в эту установку не включен. Если пакет SDK установлен на рабочем компьютере и не добавлен к коллекции электронной документации, то ссылки на содержимое пакета SDK, имеющиеся в этом разделе, работать не будут. Установите пакет .NET Framework SDK. После установки включите SDK в коллекцию электронной документации и в оглавление, следуя инструкциям в разделе [установка .NET Framework SDK](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx).  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Общеязыковая среда выполнения &#40;CLR&#41; интеграции](common-language-runtime-integration-overview.md)  
 Содержит общие сведения о среде CLR и описывает способы и преимущества использования технологии в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Описывает преимущества использования среды CLR для создания объектов базы данных.  
  
 [Сборки (компонент Database Engine)](assemblies-database-engine.md)  
 Описывает использование в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сборок для развертывания функций, хранимых процедур, триггеров, пользовательских статистических функций и определяемых пользователем типов данных, написанных на одном из языков управляемого кода, поддерживаемых средой CLR [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, а не на языке [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 [Построение объектов базы данных с помощью среды CLR &#40;CLR&#41; интеграции](database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 Описывает виды объектов, которые можно строить с использованием среды CLR, и рассматривает требования к построению объектов баз данных CLR.  
  
 [Доступ к данным из объектов среды CLR для работы с базами данных](data-access/data-access-from-clr-database-objects.md)  
 Описывает, как подпрограмма CLR может обращаться к данным, хранящимся в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Безопасность интеграции со средой CLR](security/clr-integration-security.md)  
 Описывает модель безопасности для средств интеграции со средой CLR.  
  
 [Отладка объектов базы данных среды CLR](debugging-clr-database-objects.md)  
 Описывает ограничения и требования для отладки объектов базы данных CLR.  
  
 [Развертывание объектов базы данных CLR](deploying-clr-database-objects.md)  
 Описывает развертывание сборок на рабочих серверах.  
  
 [Управление сборками интеграции со средой CLR](assemblies/managing-clr-integration-assemblies.md)  
 Описывает способы создания и удаления сборок интеграции со средой CLR.  
  
 [Мониторинг и устранение неполадок управляемых объектов базы данных](monitoring-and-troubleshooting-managed-database-objects.md)  
 Данный раздел содержит информацию о средствах, которые можно использовать для наблюдения и диагностики управляемых объектов базы данных и сборок, работающих в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Сценарии использования и примеры интеграции со средой CLR](../../database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
 Описывает сценарии использования и образцы кода, использующие объекты CLR.  
  
## <a name="see-also"></a>См. также  
 [Сборки &#40;компонент Database Engine&#41;](assemblies-database-engine.md)   
 [Установка .NET Framework SDK](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)  
  
  