---
title: Заметки о выпуске элементов управления средства просмотра отчетов SSRS
ms.date: 09/20/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maggies
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: d6c7130e45e535ad1849bed5713313bf6f89020f
ms.sourcegitcommit: 071065bc5433163ebfda4fdf6576349f9d195663
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71923810"
---
# <a name="release-notes-for-the-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>Заметки о выпуске для элементов управления средства просмотра отчетов для WebForms и WinForms в службах SSRS

Это заметки о выпуске для средств просмотра отчетов WebForms и WinForms, связанных с [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS).

Заметки о выпуске для SSRS см. в разделе [заметки о выпуске для SQL Server Reporting Services (SSRS) 2017 и более поздних версий](../release-notes-reporting-services.md).

## <a name="15013580"></a>150.1358.0
| Изменить описание | Сведения |
| :----------------- | :------ |
| Исправления ошибок | Отменено изменение, которое удалило сборки Microsoft. ReportViewer. Design из ссылок проекта. |
|           | В рамках других изменений две сборки были изменены с версии 15,0 до 15,3. Это было отменено. |
| &nbsp; | &nbsp; |

## <a name="15013570"></a>150.1357.0
| Изменить описание | Сведения |
| :----------------- | :------ |
| Исправления ошибок  | Правильная Предварительная версия для монитора с высоким разрешением |
|            | Диалоговое окно печати будет отображаться вне видимого пространства |
|            | Большое количество параметров привело к неправильной работе полос прокрутки параметров и раскрывающихся списков |
|            | Исправлена проблема с параметрами NULL и даты и времени |
|            | Обновление JQuery до версии 3.3.1 |
|            | Исправлено перекрытие с ячейками табликса в отрисовке HTML |
|            | Удалены ссылки проекта времени разработки, чтобы исключить из проектов ошибочные и неправильные сборки VS. |
|            | Исправление специальных возможностей для панели инструментов для внесения в комментарий только активных элементов |
| &nbsp; | &nbsp; |

## <a name="15900148"></a>15.900.148

| Изменить описание | Сведения |
| :----------------- | :------ |
| Исправлены ошибки, препятствующие загрузке отчетов без параметров через **Server.LoadReportDefinition**. | &nbsp; |
| Элемент управления средства просмотра отчетов WebForms. | Поддерживает внедрение на страницах с написанием справа налево (на страницах, которые изменяют поток текста с помощью свойства CSS *direction: rtl;* ).<br/><br/>Поддерживает настройку печатного текста в диалоговом окне с помощью интерфейса локализации *IReportViewerMessages5*.<br/><br/>Улучшена поддержка специальных возможностей.<br/><br/>&bull; &nbsp; &nbsp; [пакет NuGet для элемента управления "средство просмотра отчетов" WebForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| Элемент управления средства просмотра отчетов WinForms. | Исправлены ошибки при печати, когда приложение выполняется в режиме высокого разрешения.<br/><br/>&bull; &nbsp; &nbsp; [пакет NuGet для элемента управления средства просмотра отчетов WinForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>Следующие шаги

[Начало работы](integrating-reporting-services-using-reportviewer-controls-get-started.md) с элементами управления средства просмотра отчетов.

Остались вопросы? [Посетите форум Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
