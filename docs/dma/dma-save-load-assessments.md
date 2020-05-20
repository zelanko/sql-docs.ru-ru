---
title: Сохранение и загрузка оценок с помощью Помощник по миграции данных
description: Узнайте, как использовать Помощник по миграции данных для сохранения и загрузки оценок.
ms.date: 01/10/2020
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.custom: seo-lt-2019
ms.openlocfilehash: 02a6d49202ad2607d862246eee232e599788244a
ms.sourcegitcommit: fb1430aedbb91b55b92f07934e9b9bdfbbd2b0c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2020
ms.locfileid: "82885861"
---
# <a name="save-and-load-assessments-with-data-migration-assistant"></a>Сохранение и загрузка оценок с помощью Помощник по миграции данных

Следующие пошаговые инструкции помогут вам использовать Помощник по миграции данных версии 5.0 или более поздней, чтобы сохранить оценку базы данных в файле, а затем загрузить оценку из файла.

> [!NOTE]
> Помимо загрузки оценок, сохраненных с помощью последней версии DMA, пользователи также могут использовать эту функцию для загрузки оценок, экспортированных в виде JSON файлов из предыдущих версий Помощник по миграции данных для просмотра результатов в версии 5.0 и более поздних версиях.

## <a name="saving-an-assessment-to-a-file"></a>Сохранение оценки в файл

1. После выполнения оценки с помощью Помощник по миграции данных выберите **сохранить оценку**.

   ![Открытие диалогового окна «сохранение оценки»](../dma/media/dma-save-load-assessments/dma-open-save-dialog.png)

   Стандартное **Сохранение...** Откроется диалоговое окно.

   > [!NOTE]
   > Дополнительные сведения о выполнении оценки в Помощник по миграции данных см. в статье [выполнение оценки миграции SQL Server с помощник по миграции данных](../dma/dma-assesssqlonprem.md).

2. Укажите имя файла и нажмите кнопку **сохранить**.

   ![Именование и сохранение файла оценки](../dma/media/dma-save-load-assessments/dma-name-save-assessment.png)

## <a name="loading-an-assessment-saved-to-a-file"></a>Загрузка оценки, сохраненной в файл

1. Чтобы загрузить оценку, которая ранее сохранялась в файл, запустите Помощник по миграции данных, а затем на вкладке **все оценки** выберите пункт **Оценка нагрузки**.

   ![Открытие диалогового окна «Оценка нагрузки»](../dma/media/dma-save-load-assessments/dma-open-load-dialog.png)

2. Перейдите к сохраненному файлу оценки, который требуется загрузить, выберите файл и нажмите кнопку **Открыть**.

   ![Открытие файла оценки](../dma/media/dma-save-load-assessments/dma-open-assessment.png)

   На вкладке **все оценки** появится запись для загружаемой оценки.

   ![Отображение записи оценки](../dma/media/dma-save-load-assessments/dma-display-assessment-entry.png)

3. Выберите запись оценки, а затем щелкните **Открыть оценку**.

   ![Открытие сведений об оценке](../dma/media/dma-save-load-assessments/dma-open-assessment-detail.png)

   Помощник по миграции данных теперь отображает подробные сведения об оценке, которая была выполнена ранее.

   ![Отображение сведений о оценке](../dma/media/dma-save-load-assessments/dma-display-assessment-detail.png)
