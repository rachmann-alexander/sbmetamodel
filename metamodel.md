@startuml
class ServiceBlueprintModel {
  + name: String
  + version: String
}

abstract class ServiceElement {
  + label: String
}

abstract class ActiveServiceElement {
}

class Activity {
}

class Failure {
}

class Sequence {
}

class Evidence {
}

class Line {
  + type: LINE_TYPE
}

enum LINE_TYPE {
  VISIBILITY
  AUDIBILITY
  INTERACTION
  INTERNAL_INTERACTION
  ORDER_PENETRATION
  IMPLEMENTATION
}

ServiceBlueprintModel "1" *--> "1..*" ServiceElement

ServiceElement <|-- ActiveServiceElement
ServiceElement <|-- Sequence
ServiceElement <|-- Line

ActiveServiceElement <|-- Activity
ActiveServiceElement <|-- Failure
ActiveServiceElement <|-- Evidence


Sequence "1 from" --> ActiveServiceElement
Sequence "1 to" --> ActiveServiceElement
ServiceElement "1 aboveLine" --> Line
@enduml
