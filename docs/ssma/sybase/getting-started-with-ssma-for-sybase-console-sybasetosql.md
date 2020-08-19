---
description: Начало работы с помощью консоли SSMA для Sybase (SybaseToSQL)
title: Начало работы с помощью консоли SSMA для Sybase (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: e59cb5565ca518dc927f29e684401bf8fc6d5822
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418320"
---
# <a name="getting-started-with-the-ssma-for-sybase-console-sybasetosql"></a>Начало работы с помощью консоли SSMA для Sybase (SybaseToSQL)
В этом разделе описывается процедура запуска и начала работы с консольным приложением SSMA для Sybase. Здесь также перечислены соглашения, используемые в типичном окне вывода консоли SSMA.  
  
## <a name="launching-the-ssma-console"></a>Запуск консоли SSMA  
Чтобы запустить консольное приложение SSMA, выполните следующие действия:  
  
1.  Последовательно выберите пункты Пуск и все программы.  
  
2.  Щелкните ярлык **командной строки Sybase помощник по миграции SQL Server** .  
  
    В нем отображается меню использования консоли SSMA и `(/? Help)` , которое поможет приступить к работе с консольным приложением.  
  
## <a name="using-the-ssma-console"></a>Использование консоли SSMA  
После успешного запуска консоли в системе Windows для работы с ней можно выполнить следующие действия.  
  
1.  Настройте консоль SSMA с помощью файлов скриптов. Дополнительные сведения об этом разделе см. в разделе [Создание файлов скриптов &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
2.  [Создание файлов переменных значений &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [Создание файлов подключения к серверу &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [Выполняя консоль SSMA &#40;SybaseToSQL&#41;](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) в соответствии с потребностями проекта. 
  
Дополнительные функции:  
  
1.  [Укажите пароль](managing-passwords-sybasetosql.md) и экспортируйте или импортируйте его на другие компьютеры.  
  
2.  [Создание отчетов](generating-reports-sybasetosql.md) для просмотра подробных отчетов в формате XML для оценки, преобразования и переноса данных. Кроме того, можно создавать подробные отчеты об ошибках для команд обновления и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
После выполнения команд и параметров сценария SSMA консольная программа отображает результаты и сообщения (сведения, ошибку и т. д.) пользователю на консоли или, при необходимости, перенаправляет в выходной XML-файл. Каждый тип сообщения в выходных данных обозначается уникальным цветом. Например, текстовое сообщение в белом цвете означает команды файла сценария; зеленый цвет представляет собой запрос на ввод пользователя и т. д.  
  
![Вывод консоли SSMA_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "Вывод консоли SSMA_Sybase")  
  
В следующей таблице представлена цветовая интерпретация выходных данных консоли.  
  
|Color|Description|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Отметка даты и времени, сообщение пользователю|  
|White|Команды файла сценария, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Запрос на ввод данных пользователем|  
|Цвет|Начало, окончание и результат операции|  
  
## <a name="see-also"></a>См. также раздел  
[Установка SSMA для SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
