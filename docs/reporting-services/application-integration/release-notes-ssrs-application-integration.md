---
title: Заметки о выпуске элементов управления средства просмотра отчетов
description: Заметки о выпуске элементов управления средства просмотра отчетов WebForms и WinForms, связанных с Reporting Services.
ms.date: 01/16/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.custom: seo-lt-2019
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maggies
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: 5ee9bd80519e9dc9d75bb78a98b548b2a60ef247
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "76259382"
---
# <a name="release-notes-for-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>Заметки о выпуске элементов управления средства просмотра отчетов WebForms и WinForms в SSRS

Это заметки о выпуске элементов управления средства просмотра отчетов WebForms и WinForms, связанных с [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS).

Заметки о выпуске SSRS см. в статье [Release notes for SQL Server Reporting Services (SSRS) 2017 and later](../release-notes-reporting-services.md) (Заметки о выпуске SQL Server Reporting Services (SSRS) 2017 и более поздних версий)

## <a name="15014000"></a>150.1400.0
| Описание изменения | Сведения |
| :----------------- | :------ |
| Исправления ошибок | Исправлена проблема, при которой элемент управления "средство просмотра" не загружался в режиме конструктора. |
| &nbsp; | &nbsp; |

## <a name="15013580"></a>150.1358.0
| Описание изменения | Сведения |
| :----------------- | :------ |
| Исправления ошибок | Отменено изменение, которое удаляло сборки Microsoft.ReportViewer.Design из ссылок проекта. |
|           | В рамках других изменений две сборки изменены с версии 15.0 до 15.3. Это изменение отменено. |
| &nbsp; | &nbsp; |

## <a name="15013570"></a>150.1357.0
| Описание изменения | Сведения |
| :----------------- | :------ |
| Исправления ошибок  | Правильный предварительный просмотр для монитора с высоким разрешением |
|            | Диалоговое окно печати будет отображаться вне видимого пространства |
|            | Большое количество параметров привело к неправильной работе полос прокрутки параметров и раскрывающихся списков |
|            | Исправлена проблема с параметрами NULL и даты и времени |
|            | Обновление JQuery до версии 3.3.1 |
|            | Исправлено перекрытие с ячейками табликса в отрисовке HTML |
|            | Удалены ссылки проекта времени разработки, чтобы исключить из проектов ошибочные и неправильные сборки VS |
|            | Исправление специальных возможностей для панели инструментов для внесения в комментарий только активных элементов |
| &nbsp; | &nbsp; |

## <a name="150900148"></a>150.900.148

| Описание изменения | Сведения |
| :----------------- | :------ |
| Исправлены ошибки, препятствующие загрузке отчетов без параметров через **Server.LoadReportDefinition**. | &nbsp; |
| Элемент управления средства просмотра отчетов WebForms. | Поддерживает внедрение на страницах с написанием справа налево (на страницах, которые изменяют поток текста с помощью свойства CSS *direction: rtl;* ).<br/><br/>Поддерживает настройку печатного текста в диалоговом окне с помощью интерфейса локализации *IReportViewerMessages5*.<br/><br/>Улучшена поддержка специальных возможностей.<br/><br/>&bull; &nbsp; &nbsp; [Пакет NuGet для элемента управления "средство просмотра отчетов" WebForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| Элемент управления средства просмотра отчетов WinForms. | Исправлены ошибки при печати, когда приложение выполняется в режиме высокого разрешения.<br/><br/>&bull; &nbsp; &nbsp; [Пакет NuGet для элемента управления "средство просмотра отчетов" WinForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>Дальнейшие действия

[Начало работы](integrating-reporting-services-using-reportviewer-controls-get-started.md) с элементами управления средства просмотра отчетов.

Остались вопросы? [Посетите форум Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
