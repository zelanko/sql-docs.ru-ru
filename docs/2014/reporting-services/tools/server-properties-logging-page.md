---
title: Свойства сервера (страница "Ведение журнала") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a04c27fd790a1ad5c4ba453b43af5983a6440e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099531"
---
# <a name="server-properties-logging-page"></a>Свойства сервера (страница «Регистрация»)
  Эта страница используется для задания предельных значений данных, собираемых сервером отчетов при выполнении отчета. Данные выполнения сохраняются самим приложением в базе данных сервера отчетов. Предусмотрена возможность отслеживать действия с отчетами применительно к серверу отчетов, который работает в собственном режиме или в режиме интеграции с SharePoint. Если сервер отчетов представляет собой часть масштабного развертывания, то в журнале выполнения отчета ведется регистрация всех действий с отчетами для всего проекта развертывания в виде одного файла журнала.  
  
 Чтобы открыть эту страницу, запустите среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], подключитесь к серверу отчетов, щелкните правой кнопкой мыши имя сервера отчетов и выберите **Свойства**. Нажмите кнопку **Ведение журнала** , чтобы открыть эту страницу.  
  
## <a name="options"></a>Параметры  
 **Включить ведение журнала выполнения отчетов**  
 Щелкните, чтобы создать и сохранить данные о действиях с отчетами на сервере. Если этот параметр включен, то сервер отчетов отслеживает используемые отчеты, частоту выполнения отчетов, типы выполненных операций с отчетами, форматы вывода и тех, кто вызвал отчет на выполнение. Дополнительные сведения о дополнительных точках данных, записанных в журнал, см. в разделе [Журнал выполнения сервера отчетов и представление ExecutionLog3](../report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **Удалить записи журнала старше этого числа дней**  
 Задается количество дней, после которого записи журнала будут удалены из журнала выполнения отчета. Значение по умолчанию — 60 суток.  
  
## <a name="see-also"></a>См. также:  
 [Установка свойств сервера отчетов (среда Management Studio)](set-report-server-properties-management-studio.md)   
 [Подключение к серверу отчетов в среде Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Файлы и источники журналов служб Reporting Services](../report-server/reporting-services-log-files-and-sources.md)   
 [Справка F1 по использованию сервера отчетов среде Management Studio](report-server-in-management-studio-f1-help.md)   
 [Журнал выполнения сервера отчетов и представление ExecutionLog3](../report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
