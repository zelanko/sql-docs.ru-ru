---
title: Управление сборками интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: f9acc56d72d2ed994f497676813e45ef0a914431
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953785"
---
# <a name="managing-clr-integration-assemblies"></a>Управление сборками интеграции со средой CLR
  Управляемый программный код компилируется и развертывается в виде модулей, которые называются сборками. Сборка упакована в виде динамической библиотеки или исполняемого файла (.exe). Исполняемый файл можно запускать, а для вызова динамической библиотеки нужно подключить ее к существующему приложению. Управляемые сборки DLL могут загружаться в и размещаться в [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]база данных с помощью инструкции CREATE ASSEMBLY, прежде чем ее можно будет загрузить в процесс и использовать. Сборки можно обновлять до более новой версии с помощью инструкции ALTER ASSEMBLY, а также удалять из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции DROP ASSEMBLY.  
  
 Информация о сборке хранится в таблице `sys.assembly_files` в базе данных, где установлена сборка. Таблица `sys.assembly_files` содержит следующие столбцы.  
  
|Столбец|Описание|  
|------------|-----------------|  
|assembly_id|Идентификатор, определенный для сборки. Это число назначается всем объектам, относящимся к одной сборке.|  
|name|Имя объекта.|  
|file_id|Идентификационный номер каждого из объектов. Первый объект, связанный с данным идентификатором сборки `assembly_id`, получает номер 1. Если существует несколько объектов, связанных с одним и тем же `assembly_id`, то каждое последующее значение `file_id` увеличивается на 1.|  
|содержимое|Шестнадцатеричное представление сборки или файла.|  
  
## <a name="in-this-section"></a>В этом разделе  
 [Создание сборки](creating-an-assembly.md)  
 Обсуждается создание сборок с ключевыми словами SAFE, EXTERNAL_ACCESS и UNSAFE CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Изменение сборки](altering-an-assembly.md)  
 Описывается обновление сборок CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Удаление сборки](dropping-an-assembly.md)  
 Описывается удаление сборок CLR из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Безопасность интеграции со средой CLR](../security/clr-integration-security.md)   
 [Управление доступом для кода на основе интеграции со средой CLR](../security/clr-integration-code-access-security.md)  
  
  
