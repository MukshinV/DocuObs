Итерация 1:
Самое простое решение.
PCG объект позволяет переопределять ISM(InstancedStaticMesh) объект на каждый ассет. Это в целом не удобно, тк необходимо каждому пропсу указывать его ISM класс.
С другой стороны именно указанием F3_ISM класса можно показывать, какие объекты в PCG являются интерактивными.

Здесь есть 2 уровня абстракции:

1. F3_BannedInstancesManager Глобальный менеджер интерактивных ISM объектов. Этот менеджер доступен всем F3_ISM объектам, он хранит индексы всех забаненных инстансов и обновляет F3_ISM компоненты, после того как инстанс должен вернуться на свое место.
Также F3_BannedInstancesManager занимается хранением этой информации на диске, севгейме и рассылает эти данные по сети другим игрокам.

2. F3_ISM Интерактивный ISM компонент. Он ведет себя так же как и обычный ISM компонент за исключением того, что он может маскировать инстансы, забаненые F3_BannedInstancesManager.

Когда F3_BannedInstancesManager оповещает F3_ISM о новом забаненном инстансе, ?кто-то? создает новый интерактивный объект на месте забаненного инстанса, при этом нужно учитвать трансформацию инстанса, что указывает на то, что F3_BannedInstancesManager 
должен обладать фабрикой, которая будет создавать интерактивные объекты на месте забаненных инстансов.

Хранение F3_BannedInstancesManager:
---

Ограничения:
Плагин PCG находится в бетта версии. PSGComponent защищен от переропределения, что было бы удобно, для добавления ему игровой логики. Это позволило бы добавить игровые задачи PCG системе и избежать лишних кастов на класс ISM.

