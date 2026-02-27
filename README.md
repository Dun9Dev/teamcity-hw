# Домашнее задание к занятию 11 «Teamcity» - Шестовских Даниил

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

![](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_7.png)
## Основная часть

1. Создайте новый проект в teamcity на основе fork.
   ![img](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_20260226_211621.png)
2. Сделайте autodetect конфигурации.
3. Сохраните необходимые шаги, запустите первую сборку master.
   ![img](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_20260226_211855.png)
4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.
   ![img](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_20260226_214213.png)
6. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
8. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
9. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.
    ![img](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_20260226_232550.png)
11. Мигрируйте `build configuration` в репозиторий.
12. Создайте отдельную ветку `feature/add_reply` в репозитории.
    ![img](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_20260226_233946.png)
14. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
15. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
16. Сделайте push всех изменений в новую ветку репозитория.
17. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.
18. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
    ![img](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_20260227_000327.png)
20. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.
21. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
    ![img](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_20260227_001155.png)
23. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.
    ![img](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_20260227_002848.png)
25. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
    ![img](https://github.com/Dun9Dev/teamcity-hw/blob/main/img/Screenshot_20260227_002952.png)
27. В ответе пришлите ссылку на репозиторий.
