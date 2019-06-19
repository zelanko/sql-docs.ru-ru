---
title: Создание файлов дампа для выполнения пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 08/24/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 61ef1731-cb3a-4afb-b4a4-059b04aeade0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e1d4761db172138eb86e3cf511b904c5b86b90c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65713753"
---
# <a name="generating-dump-files-for-package-execution"></a>Создание файлов дампа для выполнения пакетов

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]позволяют создавать отладочные файлы дампа с информацией о выполнении пакета. Данные, содержащиеся в этих файлах, могут помочь с устранением неполадок при выполнении пакетов.  
  
> **Примечание.** Отладочные файла дампа могут содержать конфиденциальные сведения. Чтобы защитить конфиденциальные сведения, можно ограничить доступ к этим файлам с помощью списка управления доступом (ACL) или скопировать их в папку, доступ к которой ограничен. Например, прежде чем отправлять отладочные файлы в службу технической поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] , рекомендуется удалить из них все конфиденциальные сведения.  
  
 После развертывания проекта на сервере службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно создать файл дампа, который предоставит сведения о выполнении пакетов, содержащихся в проекте. После завершения процесса ISServerExec.exe, создаются файлы дампа. Выбрав параметр **Дамп при ошибках** в диалоговом окне **Выполнение пакета** , вы можете указать, что файл дампа будет создаваться при возникновении ошибки во время выполнения пакета. Кроме того, вы можете использовать следующие хранимые процедуры.  
  
-   [catalog.set_execution_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
     Вызовите эту хранимую процедуру для настройки файла дампа, который будет создан при возникновении любой ошибки или события и при возникновении конкретных событий во время выполнения пакета.  
  
-   [catalog.create_execution_dump](../../integration-services/system-stored-procedures/catalog-create-execution-dump.md)  
  
     Вызовите эту хранимую процедуру для приостановки выполняемого пакета и создания файла дампа.  
  
 Если вы используете модель развертывания пакетов, для указания параметра дампа отладки в командной строке создаются отладочные файлы дампа с помощью служебной программы **dtexec** или **dtutil** . Дополнительные сведения см. в статьях [Программа dtexec](../../integration-services/packages/dtexec-utility.md) и [Программа dtutil](../../integration-services/dtutil-utility.md). Дополнительные сведения о моделях развертывания пакетов см. в разделах [Развертывание проектов и пакетов служб Integration Services (SSIS)](https://msdn.microsoft.com/library/hh213290.aspx) и [Устаревшее развертывание пакетов &#40;службы SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md).   
  
## <a name="debug-dump-file-format"></a>Формат отладочного файла дампа  
 Если указывается параметр создания дампа отладки, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают следующие отладочные файлы дампа:  
  
-   Отладочный файл дампа с расширением MDMP. Этот файл имеет двоичный формат.  
  
-   Отладочный файл дампа с расширением TMP. Этот файл имеет текстовый формат.  
  
 По умолчанию службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] хранят эти файлы в папке *\<диск>:* \Program Files\Microsoft SQL Server\110\Shared\ErrorDumps.  
  
 В следующей таблице приведено описание лишь некоторых разделов TMP-файла. Этот файл также содержит дополнительные данные, не описанные в этой таблице.  
  
|Тип сведений|Описание|Пример|  
|-------------------------|-----------------|-------------|  
|Среда|Версия операционной системы, данные об использовании памяти, идентификатор и имя образа процесса. В начале TMP-файла содержатся сведения о среде.|# SSIS текстовый дамп выполнен в 13.9.2007 13:50:34<br /><br /> #PID 4120<br /><br /> #Image Name [C:\Program Files\Microsoft SQL Server\110\DTS\Binn\DTExec.exe]<br /><br /> # ОС основная=6 дополнительная=0 сборка=6000<br /><br /> # Работает на 2 процессорах AMD64 на подсистеме WOW64<br /><br /> # Память: занято 58%. Физическая: 845 МБ/2044 МБ. Виртуальная: 2404М/4095М (доступно/всего).|  
|Путь и номер версии DLL-библиотеки|Путь и номер версии каждой из DLL-библиотек, загруженных системой при обработке пакета.|# Загружен модуль: c:\bb\Sql\DTS\src\bin\debug\i386\DTExec.exe (10.0.1069.5)<br /><br /> # Загруженный модуль: C:\Windows\SysWOW64\ntdll.dll (6.0.6000.16386)<br /><br /> # Загруженный модуль: C:\Windows\syswow64\kernel32.dll (6.0.6000.16386)|  
|Последние сообщения|Последние сообщения, выданные системой. Содержат время, тип, описание и идентификатор потока для каждого сообщения.|[M:1]   Элемент кольцевого буфера:              (*pRecord)<br /><br /> [D:2]      <<\<CRingBufferLogging::RingBufferLoggingRecord>>> ( \@ 0282F1A8 )<br /><br /> [E:3]         Метка времени: 2007-09-13 13:50:32.786      (szTimeStamp)<br /><br /> [E:3]         Идентификатор потока: 2368           (ThreadID)<br /><br /> [E:3]         Имя события: OnError                        (EventName)<br /><br /> [E:3]         Имя источника:                (SourceName)<br /><br /> [E:3]         Идентификатор источника:                        (SourceID)<br /><br /> [E:3]         Идентификатор выполнения:                 (ExecutionGUID)<br /><br /> [E:3]         Код данных: -1073446879              (DataCode)<br /><br /> [E:3]         Описание: Компонент не обнаружен, не зарегистрирован, не может быть обновлен, или в нем отсутствуют необходимые интерфейсы. Контактная информация для этого компонента: "".|  
  
## <a name="related-information"></a>Дополнительные сведения  
 [Диалоговое окно «Выполнение пакета»](../../integration-services/packages/run-integration-services-ssis-packages.md#execute_package_dialog)  
  
  
