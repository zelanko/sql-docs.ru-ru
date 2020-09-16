---
title: Свойства служб SQL Server Integration Services (вкладка «Служба»)
description: Сведения о параметрах на вкладке "Служба" в диалоговом окне свойств Integration Services, таких как путь к двоичному файлу, имя узла и режим запуска.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 98a8cda889ba282079560d0c9f49793454a44f85
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88901189"
---
# <a name="sql-server-integration-services-properties-service-tab"></a>Свойства служб SQL Server Integration Services (вкладка «Служба»)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  Используйте вкладку **Службы** в диалоговом окне **Свойства** в [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], чтобы просмотреть или указать следующие параметры.  
  
## <a name="options"></a>Параметры  
 **Путь к двоичным файлам**  
 Отображает расположение программных файлов, используемых этой службой.  
  
 **Контроль ошибок**  
 1 означает `SERVICE_ERROR_NORMAL`. Если службе не удалось запуститься при запуске компьютера, программа запуска заносит в журнал сообщение об ошибке и выдает всплывающее сообщение об ошибке, но продолжает выполнять операцию запуска. Это значение невозможно изменить.  
  
 **Код завершения**  
 Код ошибки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows определяет любые проблемы, возникшие при запуске или остановке службы. Этому свойству присваивается значение **ERROR_SERVICE_SPECIFIC_ERROR** (1066), если ошибка является уникальной для службы, представленной этим классом, а сведения об ошибке доступны в свойстве **ServiceSpecificExitCode** . Во время выполнения и после нормального завершения работы служба присваивает этому параметру значение NO_ERROR (0).  
  
 **Host Name**  
 Отображает имя компьютера или кластера, где запущена служба [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **имя**;  
 Указывает отображаемое имя службы.  
  
 **Идентификатор процесса**  
 Отображает идентификатор процесса Windows.  
  
 **Тип службы SQL**  
 Отображает тип службы, предоставленной для вызывающих процессов. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает несколько служб.  
  
 **Режим запуска**  
 Установите для этой службы один из следующих вариантов:  
  
-   Вручную: Эта служба не запускается автоматически при запуске компьютера. Необходимо запустить службу при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или другого средства.  
  
-   Автоматически. Выполняется попытка запуска службы при запуске компьютера.  
  
-   Отключено. Служба не может быть запущена.  
  
 **Состояние**  
 Указывает, была ли служба запущена, остановлена или отключена. **…** указывает, что ожидается изменение состояния.  
  
  
