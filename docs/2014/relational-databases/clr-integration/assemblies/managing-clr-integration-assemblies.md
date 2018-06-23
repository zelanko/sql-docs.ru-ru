---
title: Управление сборками интеграции со средой CLR | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3cc471d26701fb71cac53645ee16d4f5bff41c44
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189336"
---
# <a name="managing-clr-integration-assemblies"></a>Управление сборками интеграции со средой CLR
  Управляемый программный код компилируется и развертывается в виде модулей, которые называются сборками. Сборка упакована в виде динамической библиотеки или исполняемого файла (.exe). Исполняемый файл можно запускать, а для вызова динамической библиотеки нужно подключить ее к существующему приложению. Управляемые DLL-сборки можно загрузить в и размещенной [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] База данных с помощью инструкции CREATE ASSEMBLY, прежде чем загруженных в отлаживаемый процесс и использовать. Сборки можно обновлять до более новой версии с помощью инструкции ALTER ASSEMBLY, а также удалять из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции DROP ASSEMBLY.  
  
 Информация о сборке хранится в таблице `sys.assembly_files` в базе данных, где установлена сборка. Таблица `sys.assembly_files` содержит следующие столбцы.  
  
|Столбец|Описание|  
|------------|-----------------|  
|assembly_id|Идентификатор, определенный для сборки. Это число назначается всем объектам, относящимся к одной сборке.|  
|name|Имя объекта.|  
|file_id|Идентификационный номер каждого из объектов. Первый объект, связанный с данным идентификатором сборки `assembly_id`, получает номер 1. Если существует несколько объектов, связанных с одним и тем же `assembly_id`, то каждое последующее значение `file_id` увеличивается на 1.|  
|content|Шестнадцатеричное представление сборки или файла.|  
  
## <a name="in-this-section"></a>в этом разделе  
 [Создание сборки](creating-an-assembly.md)  
 Обсуждается создание сборок с ключевыми словами SAFE, EXTERNAL_ACCESS и UNSAFE CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Изменение сборки](altering-an-assembly.md)  
 Описывается обновление сборок CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Удаление сборки](dropping-an-assembly.md)  
 Описывается удаление сборок CLR из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Безопасность интеграции со средой CLR](../security/clr-integration-security.md)   
 [Безопасность доступом для кода на основе интеграции со средой CLR](../security/clr-integration-code-access-security.md)  
  
  