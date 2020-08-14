---
title: Обзор миграции SQL Server Integration Services в Azure | Документация Майкрософт
description: Эта статья описывает процедуру и средства для миграции SQL Server Integration Services в Azure.
ms.date: 04/10/2020
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bf5aa9ee503dff3a00053365485c3ef70cc9247
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823268"
---
# <a name="migrate-on-premises-ssis-workloads-to-ssis-in-adf"></a>Миграция локальных рабочих нагрузок служб SSIS в службы SSIS в ADF

Эта статья описывает процедуру и средства, помогающие перенести рабочие нагрузки SQL Server Integration Services (SSIS) в службы SSIS в ADF.

[Общие сведения о миграции](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview) описывают общий процесс миграции рабочих нагрузок извлечения, преобразования и загрузки из локальных служб SSIS в службы SSIS в ADF.

Процесс миграции состоит из двух этапов: [оценка](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#assessment) и [миграция](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#migration).

## <a name="assessment"></a>Оценка

Помощник по миграции данных (DMA) представляет собой бесплатное скачиваемое средство для этой цели, которое можно установить и запустить локально. Можно создать проект оценки DMA типа Integration Services, чтобы оценить пакеты SSIS в пакетах и определить проблемы совместимости.

Получите [помощник по миграции баз данных](https://docs.microsoft.com/sql/dma/dma-overview) и [выполните оценку пакетов](https://docs.microsoft.com/sql/dma/dma-assess-ssis).

## <a name="migration"></a>Миграция

В зависимости от типов хранилища исходных пакетов SSIS и назначения миграции рабочих нагрузок базы данных шаги по переносу пакетов SSIS и заданий агента SQL Server, планирующих выполнение пакетов служб SSIS, могут отличаться. Дополнительные сведения см. [на этой странице](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#migration).

## <a name="next-steps"></a>Дальнейшие действия

- [Перенос пакетов Integration Services в Управляемый экземпляр SQL Azure](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages-managed-instance).
- [Перенос заданий SSIS в Фабрику данных Azure (ADF) с помощью SQL Server Management Studio (SSMS)](https://docs.microsoft.com/azure/data-factory/how-to-migrate-ssis-job-ssms).
