---
title: Управление сборками интеграции со средой CLR | Документы Microsoft
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
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
caps.latest.revision: 56
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 903e937e776de11994e37f340584bc2c22ff7801
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="managing-clr-integration-assemblies"></a>Управление сборками интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Управляемый программный код компилируется и развертывается в виде модулей, которые называются сборками. Сборка упакована в виде динамической библиотеки или исполняемого файла (.exe). Исполняемый файл можно запускать, а для вызова динамической библиотеки нужно подключить ее к существующему приложению. Управляемые DLL-сборки можно загрузить в и размещенной [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] требует, чтобы до загрузки DLL-библиотеки в процесс и использования она была зарегистрирована в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Сборки можно обновлять до более новой версии с помощью инструкции ALTER ASSEMBLY, а также удалять из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции DROP ASSEMBLY.  
  
 Сведения о сборке хранится в **sys.assembly_files** таблицы в базе данных, где установлена сборка. **Sys.assembly_files** таблица содержит следующие столбцы.  
  
|Столбец|Описание|  
|------------|-----------------|  
|assembly_id|Идентификатор, определенный для сборки. Это число назначается всем объектам, относящимся к одной сборке.|  
|имя|Имя объекта.|  
|file_id|Идентификационный номер каждого из объектов, первый объект, связанный с данной **assembly_id** присваивается значение 1. Если несколько объектов, связанных с тем же **assembly_id**, то каждое последующее **file_id** значение увеличивается на 1.|  
|content|Шестнадцатеричное представление сборки или файла.|  
  
## <a name="in-this-section"></a>В этом разделе  
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 Обсуждается создание сборок с ключевыми словами SAFE, EXTERNAL_ACCESS и UNSAFE CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Изменение сборки](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 Описывается обновление сборок CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Удаление сборки](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 Описывается удаление сборок CLR из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Безопасность интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Безопасность доступом для кода на основе интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  
