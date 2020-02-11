---
title: Управление сборками интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: b3476ba45f7f563524cdfd9855e80f9c5dd96524
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68054449"
---
# <a name="managing-clr-integration-assemblies"></a>Управление сборками интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Управляемый программный код компилируется и развертывается в виде модулей, которые называются сборками. Сборка упакована в виде динамической библиотеки или исполняемого файла (.exe). Исполняемый файл можно запускать, а для вызова динамической библиотеки нужно подключить ее к существующему приложению. Управляемые сборки DLL могут загружаться в и размещаться [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]в. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] требует, чтобы до загрузки DLL-библиотеки в процесс и использования она была зарегистрирована в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Сборки можно обновлять до более новой версии с помощью инструкции ALTER ASSEMBLY, а также удалять из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции DROP ASSEMBLY.  
  
 Сведения о сборке хранятся в таблице **sys. assembly_files** в базе данных, в которой установлена сборка. Таблица **sys. assembly_files** содержит следующие столбцы.  
  
|Столбец|Description|  
|------------|-----------------|  
|assembly_id|Идентификатор, определенный для сборки. Это число назначается всем объектам, относящимся к одной сборке.|  
|name|Имя объекта.|  
|file_id|Число, идентифицирующее каждый объект, с первым объектом, связанным с заданным **assembly_id** , которому присваивается значение 1. Если несколько объектов связаны с одним и тем же **assembly_id**, каждое последующее **file_id** значение увеличивается на 1.|  
|Содержимое|Шестнадцатеричное представление сборки или файла.|  
  
## <a name="in-this-section"></a>в этом разделе  
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 Обсуждается создание сборок с ключевыми словами SAFE, EXTERNAL_ACCESS и UNSAFE CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Изменение сборки](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 Описывается обновление сборок CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Удаление сборки](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 Описывается удаление сборок CLR из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Безопасность интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Управление доступом для кода на основе интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  
