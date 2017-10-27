---
title: "Удаление построителя отчетов | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ebfb5781c80cac35936dfdb9ad2e434ee5ca7f9e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---

# <a name="uninstall-report-builder"></a>Удаление построителя отчетов

Изолированную версию построителя отчетов можно удалить с помощью панели управления или из командной строки.

Удаление построителя отчетов из командной строки использует синтаксис, совпадающий с синтаксисом, используемым при установке построителя отчетов, за исключением того, что необходимо использовать параметр /x вместо параметра /i. Командная строка, предназначенная для удаления, может включать параметр /quiet и другие стандартные параметры. Если пакет установщика Windows для построителя отчетов (ReportBuilder3_x86.msi) был удален, то для удаления построителя отчетов пользоваться командной строкой будет неудобно. Дополнительные сведения о возможности удаления построителя отчетов с помощью его идентификатора GUID см. в документации по программе msiexec в статье [Параметры командной строки](https://msdn.microsoft.com/library/windows/desktop/aa367988.aspx).  

Если папки, используемые построителем отчетов, содержат пользовательские файлы, то при удалении построителя отчетов эти папки и файлы сохраняются. Удаляются только файлы построителя отчетов.  

### <a name="to-uninstall-report-builder-from-the-control-panel"></a>Удаление построителя отчетов с панели управления

1.  В меню **Пуск** выберите пункт **Панель управления**.  
  
2.  На панели управления щелкните элемент **Программы и компоненты**.  
  
3.  Найдите [!INCLUDE[msCoName](../../includes/msconame-md.md)] построитель отчетов SQL Server 2016 в **имя** и щелкните его.  
  
4.  Нажмите кнопку **Удалить**.  
  
5.  Если понадобится подтвердить удаление построителя отчетов, нажмите кнопку **Да**.  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a>Удаление построителя отчетов из командной строки  
  
1.  В меню **Пуск** выберите команду **Выполнить**.  
  
2.  В текстовом поле **Открыть** введите **cmd**.  
  
3.  В окне командной строки перейдите к папке, содержащей файл ReportBuilder3_x86.msi.  
  
4.  Введите следующую обычную командную строку:  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 При необходимости включения ведения журнала используйте следующую командную строку:  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
5.  Нажмите клавишу **ВВОД**.  

## <a name="next-steps"></a>Следующие шаги

[Установка построителя отчетов](../../reporting-services/install-windows/install-report-builder.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

