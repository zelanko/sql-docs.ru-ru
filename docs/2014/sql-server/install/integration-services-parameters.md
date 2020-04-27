---
title: Параметры Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 100e796bb27d1e60db000a364a0432273dd5cafb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094235"
---
# <a name="integration-services-parameters"></a>Параметры служб Integration Services
  Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]можно выполнить анализ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакетов на компьютере или [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] файлов пакета в файловой системе. При анализе файлов в файловой системе необходимо указать путь к папке, содержащей пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **Анализировать пакеты служб SSIS на компьютере**  
 Выберите этот параметр для анализа пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на компьютере. По умолчанию этот параметр выбран.  
  
 **Анализировать файлы пакетов служб SSIS**  
 Выберите этот параметр для анализа пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в файловой системе.  
  
 **Путь к пакетам служб SSIS**  
 Укажите UNC-путь или локальный адрес, по которому размещены пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Имена файлов включать не нужно. Если указанный путь недоступен, вы не сможете нажать кнопку **Далее**. По умолчанию путь пустой. Это поле доступно только при выборе пункт **Анализ файлов пакетов служб SSIS**.  
  
## <a name="see-also"></a>См. также  
 [Работа с советником по переходу](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
