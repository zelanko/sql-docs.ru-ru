---
title: Гибридный буферный пул | Документация Майкрософт
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ''
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.openlocfilehash: a8098c38b72ba44ab973fe5564b93740252bafc6
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51560311"
---
# <a name="hybrid-buffer-pool"></a>Гибридный буферный пул
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В SQL Server 2019 CTP 2.1 представлена новая функция в ядре СУБД SQL Server, которая обеспечивает прямой доступ к страницам данных в файлах базы данных, хранимых на устройствах с постоянной памятью (PMEM). 

В традиционной системе без постоянной памяти SQL Server кэширует страницы данных в буферном пуле. Благодаря гибридному буферному пулу SQL Server пропускает копирование страницы в часть буферного пула на основе DRAM и вместо этого ссылается на страницу напрямую в файле базы данных, хранящемся на PMEM-устройстве. Доступ к файлам данных в постоянной памяти для гибридного буферного пула выполняется с использованием режима MMIO. Это также называется компонентом паравиртуализации.

Прямая ссылка на PMEM-устройстве возможна только на "чистые" страницы. Когда страница становится "грязной", она хранится в DRAM и в конечном итоге переписывается обратно на PMEM.

Эта функция доступна в Windows и Linux.

## <a name="enable-hybrid-buffer-pool"></a>Включение гибридного буферного пула

В версии CTP 2.1 для использования гибридного буферного пула необходимо включить флаг трассировки при запуске 809.

## <a name="best-practices-for-hybrid-buffer-pool"></a>Рекомендации по использованию гибридного буферного пула

* При форматировании устройства с энергонезависимой памятью в Windows используйте максимальный размер единицы размещения, доступный для файловой системы NTFS (2 МБ в Windows Server 2019), и включите для устройства режим DAX (DirectAccess).
  