---
title: Ведение журнала для загрузки с балансировкой пакеты на удаленном сервере | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], remote packages
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 679554db4855b9d30d8ca3e8ae54f8756667baed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194564"
---
# <a name="logging-for-load-balanced-packages-on-remote-servers"></a>Ведение журнала для пакетов с балансировкой нагрузки на удаленных серверах
  Для администратора проще управлять журналами для всех дочерних пакетов, выполняющихся на разных серверах, когда все дочерние пакеты используют один регистратор и все они выполняют запись в одно назначение. Одним из способов создания общего файла журнала для всех дочерних пакетов является настройка дочерних пакетов на запись своих событий в регистратор служб SQL Server. Для всех пакетов можно задать использование одной базы данных, одного сервера и одного экземпляра сервера.  
  
 При просмотре журналов администратору достаточно подключиться к одному серверу, чтобы просмотреть файлы журналов для всех дочерних пакетов.  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о способах включения ведения журналов в пакете см. в разделе [Включение средств ведения журналов в SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).  
  
## <a name="see-also"></a>См. также  
 [Ведение журналов в службах Integration Services (SSIS)](performance/integration-services-ssis-logging.md)  
  
  
