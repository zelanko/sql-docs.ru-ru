---
description: Начало работы с консолью SSMA для Oracle (OracleToSQL)
title: Начало работы с SSMA для консоли Oracle (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Console, Console Output Conventions
- Oracle Console, Launching Console
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: a403f515c057349c9717422f99b6de15aede566f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463270"
---
# <a name="getting-started-with-ssma--for-oracle-console-oracletosql"></a>Начало работы с консолью SSMA для Oracle (OracleToSQL)
В этом разделе описывается процедура запуска и начала работы с консольным приложением Oracle. Здесь также перечислены соглашения, используемые в типичном окне вывода консоли SSMA.  
  
## <a name="launching-ssma-console"></a>Запуск консоли SSMA  
Чтобы запустить консольное приложение SSMA, выполните следующие действия:  
  
1.  Последовательно выберите пункты **Пуск** и **все программы**.  
  
2.  Щелкните ярлык ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для командной строки Oracle помощник по миграции** .  
  
    В нем отображается меню использования консоли SSMA и `(/? Help)` , которое поможет приступить к работе с консольным приложением.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После успешного запуска консоли в системе Windows для работы с ней можно выполнить следующие действия.  
  
1.  Настройте консоль SSMA с помощью файлов скриптов. Дополнительные сведения об этом разделе см. в разделе [Создание файлов скриптов &#40;OracleToSQL&#41;](../../ssma/oracle/creating-script-files-oracletosql.md) .  
  
2.  [Создание файлов переменных значений &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
3.  [Создание файлов подключения к серверу &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
4.  Запуск [консоли SSMA &#40;OracleToSQL&#41;](../../ssma/oracle/executing-the-ssma-console-oracletosql.md) в зависимости от потребностей проекта  
  
Дополнительные функции:  
  
1.  [Укажите пароль](managing-passwords-oracletosql.md) и экспортируйте или импортируйте его на другие компьютеры Windows  
  
2.  [Создание отчетов](generating-reports-oracletosql.md) для просмотра подробных отчетов с выходом в формате XML для оценки/конверсион и переноса данных. Подробные отчеты об ошибках также могут быть созданы для команд обновления и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
После выполнения команд и параметров сценария SSMA консольная программа отображает результаты и сообщения (сведения, ошибка и т. д.) пользователю на консоли или, если необходимо, перенаправляет в выходной XML-файл. Каждый тип сообщения в выходных данных обозначается уникальным цветом. Например, текстовое сообщение в белом цвете означает команды файла сценария; зеленый цвет представляет собой запрос на ввод пользователя и т. д.  
  
![Вывод консоли SSMA_Oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "Вывод консоли SSMA_Oracle")  
  
Цветовая интерпретация выходных данных консоли в следующей таблице:  
  
|Color|Description|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Отметка даты и времени, сообщение пользователю|  
|White|Команды файла сценария, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Запрос на ввод данных пользователем|  
|Цвет|Начало, окончание и результат операции|  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для Oracle](installing-ssma-for-oracle-oracletosql.md)  
  
