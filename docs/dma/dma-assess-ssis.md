---
title: Выполнение оценки миграции службы интеграции SQL Server (Помощник по миграции данных) | Документация Майкрософт
description: Узнайте, как использовать Помощник по миграции данных для оценки локальной службы интеграции SQL Server перед миграцией в базу данных SQL Azure или управляемый экземпляр базы данных SQL Azure.
ms.custom: ''
ms.date: 08/23/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84b498cbaf7a2f3d1118894157c17b8270259afa
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632867"
---
# <a name="perform-a-sql-server-integration-service-migration-assessment-with-data-migration-assistant"></a>Выполнение оценки миграции службы интеграции SQL Server с Помощник по миграции данных

Следующие пошаговые инструкции помогут вам выполнить первую оценку SQL Server миграции пакетов служб Integration Services (SSIS) в базу данных SQL Azure или управляемый экземпляр базы данных SQL Azure с помощью Помощник по миграции данных.

## <a name="create-an-assessment"></a>Создание оценки

1. Выберите **Новый** значок (+), а затем выберите тип проекта **оценки** в качестве **службы интеграции**.

1. Задайте тип исходного и целевого сервера.

    Выберите источник как **SQL Server**и задайте тип целевого сервера в качестве **базы данных SQL Azure** или **управляемого экземпляра базы данных SQL Azure**.

1. Нажмите кнопку **Создать**.

    ![создать оценку](media/dma-assess-ssis/dma-assess-ssis-create.png)

## <a name="connect-to-a-server"></a>Подключение к серверу

1. Используйте параметр по умолчанию и нажмите кнопку **Далее** , чтобы **выбрать источники**.
1. Введите имя экземпляра SQL Server, выберите тип проверки подлинности и задайте правильные свойства соединения.
1. Используемых Введите путь к папке, содержащей пакеты служб SSIS.
1. Используемых Введите пароль шифрования пакета, если это применимо.
1. Щелкните **Подключиться** к ИСХОДНОМу экземпляру SQL Server.
  ![добавить исходный](media/dma-assess-ssis/dma-assess-ssis-addsource.png)

## <a name="add-sources-to-assess"></a>Добавление источников для оценки

1. Выберите типы хранилища пакетов служб SSIS для оценки, а затем нажмите кнопку **Добавить**.
![добавить исходный](media/dma-assess-ssis/dma-assess-ssis-addsource-type.png)
1. Выберите **Добавить источники** , чтобы открыть всплывающее меню подключения, если требуется оценка нескольких папок.
1. Щелкните **начать оценку**.
  ![начать оценку](media/dma-assess-ssis/dma-assess-ssis-assess.png)

## <a name="view-results"></a>Просмотр результатов

Категория проблемы совместимости предоставляет частично поддерживаемые или неподдерживаемые функции, которые блокируют миграцию локальных пакетов служб SSIS в Azure-SSIS Integration Runtime. Затем он предоставляет рекомендации по устранению этих проблем.

![Просмотр результатов](media/dma-assess-ssis/dma-assess-ssis-result.png)

## <a name="next-steps"></a>Следующие шаги

- [Общие сведения о переносе локальных рабочих нагрузок служб SSIS в службы SSIS в ADF](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview)
- [Миграция пакетов SQL Server Integration Services в управляемый экземпляр базы данных SQL Azure](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages-managed-instance)
- [Повторное развертывание пакетов SQL Server Integration Services в базе данных SQL Azure](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages)
