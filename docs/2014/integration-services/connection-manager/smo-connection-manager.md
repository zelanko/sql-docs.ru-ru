---
title: Диспетчер подключений SMO | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMO
- SMO connection manager
- connection managers [Integration Services], SMO
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c38b1037e3e6e2e36dbe288682867d6b9f030545
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84920475"
---
# <a name="smo-connection-manager"></a>SMO, диспетчер соединений
  Диспетчер соединений SMO позволяет пакету подключиться к серверу SQL Management Object (SMO). Задачи пересылки, включенные в службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], используют диспетчер соединений SMO. Например, задача «Передача имен входа», пересылающая данные для входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использует диспетчер соединений SMO.  
  
 При добавлении диспетчера подключений SMO в пакет службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создадут диспетчер соединений, который установит соединение SMO во время выполнения, задаст параметры диспетчера и добавит диспетчер в коллекцию `Connections` пакета. Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `SMOServer`.  
  
 Можно настроить диспетчер соединений SMO следующим образом:  
  
-   Указать имя сервера, на котором установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Выберите режим проверки подлинности для соединения с сервером.  
  
## <a name="configuration-of-the-smo-connection-manager"></a>Настройка диспетчера соединений SMO  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера соединений SMO](../smo-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](integration-services-ssis-connections.md)  
  
  
