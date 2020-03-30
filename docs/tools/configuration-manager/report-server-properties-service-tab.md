---
title: Свойства сервера отчетов (вкладка «Службы»)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2a2e1dbf-02b9-4893-aaf0-c0e4a2c9b4f9
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 902421968723f52949b352318b864d60714a6059
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307908"
---
# <a name="report-server-properties-service-tab"></a>Свойства сервера отчетов (вкладка «Службы»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Это служба сервера отчетов [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Значения свойств, выделенные светло-серым цветом, с помощью этого приложения изменить нельзя.  
  
## <a name="options"></a>Параметры  
 **Путь к двоичным файлам**  
 Отображает расположение программных файлов, используемых этой службой.  
  
 **Контроль ошибок**  
 1 означает SERVICE_ERROR_NORMAL. Если службе не удалось запуститься при запуске компьютера, программа запуска заносит в журнал сообщение об ошибке и выдает всплывающее сообщение об ошибке, но продолжает выполнять операцию запуска. Это значение невозможно изменить.  
  
 **Код завершения**  
 При возникновении ошибки ее номер выводится в этом окне. Этот номер обеспечивает возможность устранения ошибок, используйте его для поиска в базе знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] или сообщите его службе технической поддержки.  
  
 **Host Name**  
 Отображает имя компьютера или кластера, где запущен полнотекстовый поиск.  
  
 **Название**  
 Указывает отображаемое имя службы.  
  
 **Идентификатор процесса**  
 Отображает идентификатор процесса [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Тип службы SQL**  
 Тип службы, предоставленной для вызывающих процессов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает несколько служб.  
  
 **Режим запуска**  
 Установите для этой службы один из следующих вариантов:  
  
-   Вручную. Эта служба не запускается автоматически при запуске компьютера. Необходимо запустить службу при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или другого средства.  
  
-   Автоматически. Эта служба пытается запуститься при запуске компьютера.  
  
-   Отключено. Служба не может быть запущена.  
  
 **Состояние**  
 Указывает, была ли служба запущена, остановлена или отключена.  
  
## <a name="see-also"></a>См. также:  
 [Службы SQL Server](../../tools/configuration-manager/sql-server-services.md)  
  
  
