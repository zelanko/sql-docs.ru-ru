---
title: Создание простого табличного отчета (учебник по службам SSRS) | Документы Майкрософт
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
ms.openlocfilehash: af41da75d553794019f1d01c8b8f5bb6aba80622
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "65103305"
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

**Предполагаемое время для выполнения заданий учебника:** 30 минут.

## <a name="next-steps"></a>Дальнейшие действия

[Занятие 1. Создание проекта сервера отчетов (службы Reporting Services)](lesson-1-creating-a-report-server-project-reporting-services.md)

[Занятие 2. Задание информации о соединении (службы Reporting Services)](lesson-2-specifying-connection-information-reporting-services.md)

[Занятие 3. Определение набора данных для табличного отчета (службы Reporting Services)](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)

[Занятие 4. Добавление таблицы в отчет (службы Reporting Services)](lesson-4-adding-a-table-to-the-report-reporting-services.md)

[Занятие 5. Форматирование отчета (Reporting Services)](lesson-5-formatting-a-report-reporting-services.md)

[Занятие 6. Добавление группирования и итогов (службы Reporting Services)](lesson-6-adding-grouping-and-totals-reporting-services.md)

## <a name="see-also"></a>См. также раздел

[Руководства по Reporting Services](reporting-services-tutorials-ssrs.md) (дополнительные вопросы) [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
