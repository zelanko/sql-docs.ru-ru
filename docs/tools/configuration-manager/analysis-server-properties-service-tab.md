---
title: Свойства сервера анализа данных (вкладка «Службы»)
description: Сведения о параметрах на вкладке "Служба" в диалоговом окне свойств Analysis Server, таких как путь к двоичному файлу, имя узла и режим запуска.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 8dbe4bc5-6aa9-48ee-857e-0b4ea764b9cb
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016'
ms.openlocfilehash: de79d7d8392e2d63b7b0b71f34dc55e9a8254933
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97463902"
---
# <a name="analysis-server-properties-service-tab"></a>Свойства сервера анализа данных (вкладка «Службы»)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  Эта служба представляет собой [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Она должна быть запущена для правильной работы служб [!INCLUDE[ssAS](../../includes/ssas-md.md)] . Значения свойств, окрашенные в светло-серый цвет, нельзя изменить при помощи этого приложения.  
  
## <a name="options"></a>Параметры  
 **Путь к двоичным файлам**  
 Отображает расположение программных файлов, используемых этой службой.  
  
 **Контроль ошибок**  
 1 означает `SERVICE_ERROR_NORMAL`. Если службе не удалось запуститься при запуске компьютера, программа запуска заносит в журнал сообщение об ошибке и выдает всплывающее сообщение об ошибке, но продолжает выполнять операцию запуска. Это значение невозможно изменить.  
  
 **Код завершения**  
 При возникновении ошибки ее номер выводится в этом окне. Этот номер обеспечивает возможность устранения ошибок, используйте его для поиска в базе знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] или сообщите его службе технической поддержки.  
  
 **Host Name**  
 Отображает имя компьютера или кластера, где запущены службы [!INCLUDE[ssAS](../../includes/ssas-md.md)].  
  
 **имя**;  
 Указывает отображаемое имя службы.  
  
 **Идентификатор процесса**  
 Отображает номер, используемый [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows для отслеживания процессов этой программы.  
  
 **Тип службы SQL**  
 Отображает тип службы, предоставленной для вызывающих процессов. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает несколько служб.  
  
 **Режим запуска**  
 Установите для этой службы один из следующих вариантов:  
  
-   Вручную: Эта служба не запускается автоматически при запуске компьютера. Необходимо запустить службу при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или другого средства.  
  
-   Автоматически. Выполняется попытка запуска службы при запуске компьютера.  
  
-   Отключено. Служба не может быть запущена.  
  
 **Состояние**  
 Указывает, была ли служба запущена, остановлена или отключена.  
  
  
