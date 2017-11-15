---
title: "Возможности и задачи служебной программы SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server utility [SQL Server]
- utility control point
- Utility growth rate
- Multiserver management
- UCP
- Multi-server management [SQL Server]
ms.assetid: 6e6cbd25-6b1c-4e21-9ade-4584e243fd8f
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c099214c37d6f3a2d8f1198e6f172f1a11d1b64e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-utility-features-and-tasks"></a>Функции и задачи служебной программы SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] важным требованием является возможность управления средой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в целом. В этом выпуске для удовлетворения такого требования используется концепция управления приложениями и многосерверной средой, реализованная в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="benefits-of-the-sql-server-utility"></a>Преимущества служебной программы SQL Server  
 Программа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] моделирует сущности организации, связанные с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в унифицированном представлении. Контрольные точки обозревателя и проводника служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) предоставляют администраторам целостное представление о работоспособности ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для этого используется экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , служащий точкой управления служебной программой (UCP). Благодаря сочетанию сводных и подробных данных, представленных в пункте управления программой для политик избыточной и недостаточной загрузки, а также для различных ключевых параметров, появляется возможность объединения и простого определения перегруженных ресурсов. Политики исправности являются настраиваемыми и позволяют изменить заданные в них верхние и нижние пороговые значения использования ресурсов. Можно изменять глобальные политики наблюдения или настраивать индивидуальные политики наблюдения для каждой сущности, управляемой в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="typical_scenarios"></a> Приступая к работе со служебной программой SQL Server  
 Обычно в начале работы с программой создается точка управления служебной программой (UCP), представляющий собой центральную базовую точку служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В точке управления служебной программой реализуется консолидированное представление сведений об исправности ресурсов, полученных из управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После создания точки управления служебной программой в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регистрируются экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы можно было управлять ими из этой точки управления служебной программой.  
  
 Выполнять наблюдение за каждым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложения уровня данных, управляемых программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можно с помощью определений глобальных или индивидуальных политик.  
  
## <a name="related-tasks"></a>Связанные задачи  
 Используйте следующие разделы, чтобы приступить к работе с программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает замечания по настройке сервера для выполнения программы и настройке не относящихся к программе наборов элементов сбора на одном и том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Замечания по выполнению программы, не относящиеся к прочим наборам элементов сбора на том же экземпляре SQL Server](../../relational-databases/manage/run-utility-and-non-utility-collection-sets-on-same-sql-instance.md)|  
|Описывает, как создать точку управления служебной программой SQL Server.|[Создать точку управления служебной программы SQL Server (служебная программа SQL Server)](../../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md)|  
|Описывает, как подключиться к служебной программе SQL Server.|[Подключение к служебной программе SQL Server](../../relational-databases/manage/connect-to-a-sql-server-utility.md)|  
|Описывает, как зарегистрировать экземпляр SQL Server с помощью точки управления служебной программой.|[Регистрация экземпляра SQL Server (служебная программа SQL Server)](../../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md)|  
|Описывает, как использовать обозреватель программ для управления служебной программой SQL Server.|[Использование проводника служебных программ для управления служебной программой SQL Server](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)|  
|Описывает, как наблюдать за экземплярами SQL Server в служебной программе SQL Server.|[Наблюдение за экземплярами SQL Server в служебной программе SQL Server](../../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)|  
|Описывает, как просматривать результаты политики исправности ресурсов.|[Просмотр результатов политики исправности ресурсов (служебная программа SQL Server)](../../relational-databases/manage/view-resource-health-policy-results-sql-server-utility.md)|  
|Описывает, как изменить определение политики исправности ресурсов.|[Изменение определения политики исправности ресурсов (служебная программа SQL Server)](../../relational-databases/manage/modify-a-resource-health-policy-definition-sql-server-utility.md)|  
|Описывает, как настраивать хранилище данных точки управления служебной программой.|[Настройка хранилища данных точки управления служебной программы (служебная программа SQL Server)](../../relational-databases/manage/configure-your-utility-control-point-data-warehouse-sql-server-utility.md)|  
|Описывает, как настраивать политики исправности программы.|[Настройка политик исправности (служебная программа SQL Server)](../../relational-databases/manage/configure-health-policies-sql-server-utility.md)|  
|Описывает, как настраивать компенсацию в политиках загрузки процессора.|[Уменьшение уровня шума в политиках загрузки ЦП (служебная программа SQL Server)](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)|  
|Описывает, как удалить экземпляр SQL Server из точки управления служебной программой.|[Удаление экземпляра SQL Server с помощью служебной программы SQL Server](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md)|  
|Описывает, как изменить учетную запись-посредник для программы сбора данных на управляемом экземпляре SQL Server.|[Изменение учетной записи-посредника для набора элементов сбора служебной программы на управляемом экземпляре SQL Server (служебная программа SQL Server)](../../relational-databases/manage/change-proxy-account-for-utility-collection-on-managed-sql-server.md)|  
|Описывает, как переместить точку управления служебной программой с одного экземпляра SQL Server на другой.|[Перенос точки управления служебной программой из одного экземпляра SQL Server на другой (служебная программа SQL Server)](../../relational-databases/manage/move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility.md)|  
|Описывает, как удалить точку управления служебной программой.|[Удалить точку управления служебной программой (SQL Server Utility)](../../relational-databases/manage/remove-a-utility-control-point-sql-server-utility.md)|  
|Описывает, как устранять неполадки служебной программы SQL server.|[Устранение неполадок служебной программы SQL Server](http://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453)|  
|Описывает, как устранять неполадки исправности ресурсов SQL Server.|[Устранение неполадок исправности ресурсов SQL Server (служебная программа SQL Server)](../../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)|  
|Ссылки на разделы справки F1 по UtilityExplorer.|[Справка F1 проводника служебной программы](../../relational-databases/manage/utility-explorer-f1-help.md)|  
  
  
