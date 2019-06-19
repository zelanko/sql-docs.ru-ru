---
title: Возможности и задачи служебной программы SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server utility [SQL Server]
- utility control point
- Utility growth rate
- Multiserver management
- UCP
- Multi-server management [SQL Server]
ms.assetid: 6e6cbd25-6b1c-4e21-9ade-4584e243fd8f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1d3f61904a1a820df58583212dcbd2e998dbabbd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63190426"
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
|Описывает замечания по настройке сервера для выполнения программы и настройке не относящихся к программе наборов элементов сбора на одном и том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Замечания по выполнению программы, не относящиеся к прочим наборам элементов сбора на том же экземпляре SQL Server](run-utility-and-non-utility-collection-sets-on-same-sql-instance.md)|  
|Описывает, как создать точку управления служебной программой SQL Server.|[Создать точку управления служебной программы SQL Server (служебная программа SQL Server)](create-a-sql-server-utility-control-point-sql-server-utility.md)|  
|Описывает, как подключиться к служебной программе SQL Server.|[Подключение к служебной программе SQL Server](connect-to-a-sql-server-utility.md)|  
|Описывает, как зарегистрировать экземпляр SQL Server с помощью точки управления служебной программой.|[Регистрация экземпляра SQL Server (служебная программа SQL Server)](enroll-an-instance-of-sql-server-sql-server-utility.md)|  
|Описывает, как использовать обозреватель программ для управления служебной программой SQL Server.|[Использование проводника служебных программ для управления служебной программой SQL Server](use-utility-explorer-to-manage-the-sql-server-utility.md)|  
|Описывает, как наблюдать за экземплярами SQL Server в служебной программе SQL Server.|[Наблюдение за экземплярами SQL Server в служебной программе SQL Server](monitor-instances-of-sql-server-in-the-sql-server-utility.md)|  
|Описывает, как просматривать результаты политики исправности ресурсов.|[Просмотр результатов политики исправности ресурсов (служебная программа SQL Server)](view-resource-health-policy-results-sql-server-utility.md)|  
|Описывает, как изменить определение политики исправности ресурсов.|[Изменение определения политики исправности ресурсов (служебная программа SQL Server)](modify-a-resource-health-policy-definition-sql-server-utility.md)|  
|Описывает, как настраивать хранилище данных точки управления служебной программой.|[Настройка хранилища данных точки управления служебной программы (служебная программа SQL Server)](configure-your-utility-control-point-data-warehouse-sql-server-utility.md)|  
|Описывает, как настраивать политики исправности программы.|[Настройка политик исправности (служебная программа SQL Server)](configure-health-policies-sql-server-utility.md)|  
|Описывает, как настраивать компенсацию в политиках загрузки процессора.|[Уменьшение уровня шума в политиках загрузки ЦП (служебная программа SQL Server)](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)|  
|Описывает, как удалить экземпляр SQL Server из точки управления служебной программой.|[Удаление экземпляра SQL Server с помощью служебной программы SQL Server](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)|  
|Описывает, как изменить учетную запись-посредник для программы сбора данных на управляемом экземпляре SQL Server.|[Изменение учетной записи-посредника для набора элементов сбора служебной программы на управляемом экземпляре SQL Server (служебная программа SQL Server)](change-proxy-account-for-utility-collection-on-managed-sql-server.md)|  
|Описывает, как переместить точку управления служебной программой с одного экземпляра SQL Server на другой.|[Перенос точки управления служебной программой из одного экземпляра SQL Server на другой (служебная программа SQL Server)](move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility.md)|  
|Описывает, как удалить точку управления служебной программой.|[Удалить точку управления служебной программой (SQL Server Utility)](remove-a-utility-control-point-sql-server-utility.md)|  
|Описывает, как устранять неполадки служебной программы SQL server.|[Устранение неполадок служебной программы SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md)|  
|Описывает, как устранять неполадки исправности ресурсов SQL Server.|[Устранение неполадок исправности ресурсов SQL Server (служебная программа SQL Server)](troubleshoot-sql-server-resource-health-sql-server-utility.md)|  
|Ссылки на разделы справки F1 по UtilityExplorer.|[Справка F1 проводника служебной программы](utility-explorer-f1-help.md)|  
  
  
