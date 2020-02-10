---
title: Диспетчер соединений ODBC | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c6c7ecd59bcf3a3ece0d61ecbb428bb39a80068f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62833766"
---
# <a name="odbc-connection-manager"></a>диспетчер соединений ODBC
  Диспетчер соединений ODBC позволяет пакету подключаться к разнообразным системам управления базами данных, используя открытый интерфейс взаимодействия с базами данных (ODBC).  
  
 При добавлении подключения ODBC к пакету и задании свойств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] диспетчера соединений создает диспетчер соединений и добавляет его в `Connections` коллекцию пакета. Во время выполнения диспетчер соединений рассматривается как физическое соединение с ODBC.  
  
 Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `ODBC`.  
  
 Настроить диспетчер соединений ODBC можно следующими способами:  
  
-   Предоставить строку соединения, которая ссылается на пользовательское или системное имя источника данных.  
  
-   Указать сервер, к которому нужно подключиться.  
  
-   Указать, сохранять ли соединение во время выполнения.  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>Настройка диспетчера соединений ODBC  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [Справочник по пользовательскому интерфейсу диспетчера соединений ODBC](../odbc-connection-manager-ui-reference.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](integration-services-ssis-connections.md)  
  
  
