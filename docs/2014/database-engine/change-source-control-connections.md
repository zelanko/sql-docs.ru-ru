---
title: Изменение подключений системы управления версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3d158c2a0981b6174bcb83948b10bacd1a97d1f6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188951"
---
# <a name="change-source-control-connections"></a>Изменение соединений с системой управления версиями
  При первом добавлении или открытии решения в системе управления версиями поставщик этой системы создает связь между корневой папкой локального каталога решения и соответствующей папкой на сервере.  
  
 Корневая папка (называется также унифицированным корнем) находится на стороне клиента. Эта папка содержит все файлы, входящие в решение или проект. Чтобы найти последнюю версию решения, его журнал и данные о состоянии, найдите серверную папку, расположенную на сервере управления версиями. В [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe серверные папки называются проектами.  
  
 Во многих ситуациях требуется отменить привязку или отключить решение от его серверной папки. Например, если компьютер, на котором находится поставщик управления версиями, недоступен, можно подключиться к резервному компьютеру, повторно привязать решение, подключив его к папке на резервном сервере и продолжить работу в обычном режиме. Также, если проект с управляемыми источниками разветвлен, может потребоваться связать решение с серверной папкой, в которой находится новая версия проекта.  
  
 С помощью пользовательского интерфейса поставщика управления версиями можно изменить серверную папку, к которой привязано решение. Пользовательский интерфейс системы управления версиями можно открыть непосредственно из среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a>Открытие пользовательского интерфейса системы управления версиями из среды Studio  
  
1.  На **файл** последовательно выберите пункты **системы управления версиями**, а затем нажмите кнопку **запустить Microsoft Visual SourceSafe**.  
  
## <a name="see-also"></a>См. также  
 [Основы системы управления версиями](../../2014/database-engine/source-control-basics.md)   
 [Задайте параметры системы управления версиями](../../2014/database-engine/set-source-control-options.md)   
 [Исключение файлов из системы управления версиями](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
