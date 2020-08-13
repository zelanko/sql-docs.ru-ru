---
title: Создание простого табличного отчета (учебник по службам SSRS) | Документы Майкрософт
description: Используйте конструктор отчетов в Visual Studio или SQL Server Data Tools (SSDT) для создания отчета SQL Server Reporting Services (SSRS) с разбивкой на страницы.
ms.date: 04/16/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f1549d3ba775d598902fd0fd4b5cc33bab2f54de
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245143"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a>Создание простого табличного отчета (учебник по службам SSRS)

В этом руководстве описано, как использовать средство *Конструктор отчетов* в Visual Studio и SQL Server Data Tools (SSDT). Вы создадите отчет SQL Server Reporting Services (SSRS) с разбивкой на страницы. Отчет содержит таблицу запросов, созданную на основе данных в базе данных AdventureWorks2016.

По мере работы с этим руководством вы сделаете следующее:
  
- создадите проект отчетов;
- настроите подключение к данным;
- определите запрос;
- добавите табличную область данных;
- отформатируете отчет;
- сгруппируете поля;
- просмотрите отчет;
- при необходимости опубликуете отчет.

## <a name="requirements"></a>Требования

Для работы с этим руководством должны быть установлены следующие компоненты:

- [!INCLUDE[msconame-md](../includes/msconame-md.md)] Ядро СУБД SQL Server  
- SQL Server 2016 Reporting Services (SSRS) и более поздние версии.
- База данных AdventureWorks2016.  См. подробнее о [примере баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases).
- [SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md) для Visual Studio вместе с установленным расширением Reporting Services для обеспечения доступа к *конструктору отчетов*.
  
Также необходимо иметь разрешения только на чтение для получения данных из базы данных AdventureWorks2016.

**Предполагаемое время для выполнения заданий учебника**: 30 минут.

## <a name="next-steps"></a>Дальнейшие действия

[Занятие 1. Создание проекта сервера отчетов (службы Reporting Services)](lesson-1-creating-a-report-server-project-reporting-services.md)

[Занятие 2. Задание информации о соединении (службы Reporting Services)](lesson-2-specifying-connection-information-reporting-services.md)

[Урок 3. Определение набора данных для табличного отчета (службы Reporting Services)](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)

[Занятие 4. Добавление таблицы в отчет (службы Reporting Services)](lesson-4-adding-a-table-to-the-report-reporting-services.md)

[Занятие 5. Форматирование отчета (службы Reporting Services)](lesson-5-formatting-a-report-reporting-services.md)

[Занятие 6. Добавление группирования и итогов (службы Reporting Services)](lesson-6-adding-grouping-and-totals-reporting-services.md)

## <a name="see-also"></a>См. также раздел

[Руководства по Reporting Services](reporting-services-tutorials-ssrs.md) (дополнительные вопросы) [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
