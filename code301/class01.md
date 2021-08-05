[Home](README.md)

<br>

# Introduction to React and Components

<br>

## Readings from [Component-Based Architecture](https://www.tutorialspoint.com/software_architecture_design/component_based_architecture.htm)

<br>

>Component-based architecture focuses on the decomposition of the design into individual functional or logical components. The primary objective of component-based architecture is to ensure component reusability.

<br>

### What is a Component?

<br>

- A component is a modular, portable, replaceable, and reusable set of well-defined functionality that encapsulates its implementation and exporting it as a higher-level interface.
- A component is a software object, intended to interact with other components, encapsulating certain functionality or a set of functionalities.
- A software component can be defined as a unit of composition with a contractually specified interface and explicit context dependencies only.

<br>

#### Views of a Component

<br>

1. Object-oriented view
    - A component is viewed as a set of one or more cooperating classes. Each problem domain class (analysis) and infrastructure class (design) are explained to identify all attributes and operations that apply to its implementation.

2. Conventional view
    -It is viewed as a functional element or a module of a program that integrates the processing logic, the internal data structures that are required to implement the processing logic and an interface that enables the component to be invoked and data to be passed to it.

3. Process-related view
    - In this view, the system is building from existing components maintained in a library.
        - A user interface (UI) component includes grids, buttons referred as controls, and utility components expose a specific subset of functions used in other components.
        - Other common types of components are those that are resource intensive, not frequently accessed, and must be activated using the just-in-time (JIT) approach.
        - Many components are invisible which are distributed in enterprise business applications and internet web applications such as Enterprise JavaBean (EJB), .NET components, and CORBA components.

<br>

#### Characteristics of Components

<br>

- Reusability: Components are usually designed to be reused in different situations in different applications. However, some components may be designed for a specific task.
- Replaceable: Components may be freely substituted with other similar components.
- Not context specific: Components are designed to operate in different environments and contexts.
- Extensible: A component can be extended from existing components to provide new behavior.
- Encapsulated: A A component depicts the interfaces, which allow the caller to use its functionality, and do not expose details of the internal processes or any internal variables or state.
- Independent: Components are designed to have minimal dependencies on other components.

<br>

### Principles of Component−Based Design

<br>

- A component-level design can be represented by using some intermediary representation (e.g. graphical, tabular, or text-based) that can be translated into source code.
- The design of data structures, interfaces, and algorithms should conform to well-established guidelines to help us avoid the introduction of errors.
    - The software system is decomposed into reusable, cohesive, and encapsulated component units.
    - Each component has its own interface that specifies required ports and provided ports; each component hides its detailed implementation.
    - A component should be extended without the need to make internal code or design modifications to the existing parts of the component.
    - Depend on abstractions component do not depend on other concrete components, which increase difficulty in expendability.
    - Connectors connected components, specifying and ruling the interaction among components. The interaction type is specified by the interfaces of the components.
    - Components interaction can take the form of method invocations, asynchronous invocations, broadcasting, message driven interactions, data stream communications, and other protocol specific interactions.
    - For a server class, specialized interfaces should be created to serve major categories of clients. Only those operations that are relevant to a particular category of clients should be specified in the interface.
    - A component can extend to other components and still offer its own extension points. It is the concept of plug-in based architecture. This allows a plugin to offer another plugin API.

<br>

### Component-Level Design Guidelines

<br>

> Creates a naming conventions for components that are specified as part of the architectural model and then refines or elaborates as part of the component-level model.

- Attains architectural component names from the problem domain and ensures that they have meaning to all stakeholders who view the architectural model.

- Extracts the business process entities that can exist independently without any associated dependency on other entities.

- Recognizes and discover these independent entities as new components.

- Uses infrastructure component names that reflect their implementation-specific meaning.

- Models any dependencies from left to right and inheritance from top (base class) to bottom (derived classes).

- Model any component dependencies as interfaces rather than representing them as a direct component-to-component dependency.

<br>

### Conducting Component-Level Design

<br>

- Recognizes all design classes that correspond to the infrastructure domain.

- Describes all design classes that are not acquired as reusable components, and specifies message details.

- Identifies appropriate interfaces for each component and elaborates attributes and defines data types and data structures required to implement them.

- Describes processing flow within each operation in detail by means of pseudo code or UML activity diagrams.

- Describes persistent data sources (databases and files) and identifies the classes required to manage them.

- Develop and elaborates behavioral representations for a class or component.

- Elaborates deployment diagrams to provide additional implementation detail.

- Demonstrates the location of key packages or classes of components in a system by using class instances and designating specific hardware and operating system environment.

- The final decision can be made by using established design principles and guidelines.

<br>

#### Advantages of using component based architecture

<br>

1. Ease of deployment: As new compatible versions become available, it is easier to replace existing versions with no impact on the other components or the system as a whole.

2. Reduced cost: The use of third-party components allows you to spread the cost of development and maintenance.

3. Ease of development: Components implement well-known interfaces to provide defined functionality, allowing development without impacting other parts of the system.

4. Reusable: The use of reusable components means that they can be used to spread the development and maintenance cost across several applications or systems.

5. Modification of technical complexity: A component modifies the complexity through the use of a component container and its services.

6. Reliability :The overall system reliability increases since the reliability of each individual component enhances the reliability of the whole system via reuse.

7. System maintenance and evolution: Easy to change and update the implementation without affecting the rest of the system.

8. Independent: Independency and flexible connectivity of components. Independent development of components by different group in parallel.

<br>

## Readings from [What is Props and How to Use it in React?](https://itnext.io/what-is-props-and-how-to-use-it-in-react-da307f500da0)

<br>

### What is Props?

<br>

> React is a component-based library which divides the UI into little reusable pieces. 

> In some cases, those components need to communicate (send data to each other) and the way to pass data between components is by using props.

- `Props` is a special keyword in React, which stands for `properties` and is being used for passing data from one component to another.
    - Data with props are being passed in a uni-directional flow. (one way from parent to child).
    - Props data is read-only, which means that data coming from the parent should not be changed by child components.

<br>

### Using Props in React

<br>

1. Firstly, define an attribute and its value(data).
    - We can assign attributes and values to HTML tags.
    - We can do the same for React components. We can define our own attributes & assign values with interpolation `{ }`.

<br>

    ```
    Declaring an attribute to HTML tag:

    <ChildComponent someAttribute={value} anotherAttribute={value}/>
    ```

2. Then pass it to child component(s) by using Props.
    - We pass props into a React component and props bring all the necessary data.
    - Props are arguments passed into React components.

<br>

    ```
    Passing an Argument to a Function:

    let add = (a, b) => {  
    return a + b; 
    };

    Passing and Argument to a React Component:

    let ChildComponent = (props) => {  
    return <p>I'm the 1st child!</p>; 
    };
    ```

3. Finally, render the Props Data.
    - Prop is an Object: Render the props object by using string interpolation.
    - In `Javascript` access to object elements with `dot(.) notation`.
    - Each ChildComponent renders now its own prop data.

<br>

    ```
    Rendering Props Object:

    let ChildComponent = (props) => {  
    return <p>{props.text}</p>; 
    };

    class ParentComponent extends Component {  
     render() {
        return (
        <h1>
            I'm the parent component.
            <ChildComponent text={"I'm the 1st child"} />
            <ChildComponent text={"I'm the 2nd child"} />
            <ChildComponent text={"I'm the 3rd child"} />
        </h1>
        );
    }
    }
    ```

<br>

### Conclusion

<br>

- What is a component?
    - A component is a modular, portable, replaceable, and reusable set of well-defined functionality that encapsulates its implementation and exporting it as a higher-level interface. It is also a software object, intended to interact with other components, encapsulating certain functionality or a set of functionalities.

- What are the charactistics of a component?
    - Reusability
    - Replaceable
    - Not context specific
    - Extensible
    - Encapsulated
    - Independent

- What are the advantages of using component based architecture?
    - Ease of deployment
    - Reduced cost
    - Ease of development
    - Reusable
    - Modification of technical complexity
    - Reliability
    - System maintenance and evolution
    - Independent

- What is props short for?
    - “Props” is a special keyword in React, which stands for properties and is being used for passing data from one component to another.

- How are props used in React?
    - Define an attribute and its value(data).
    - Pass it to child component(s) by using Props.
    - Render the Props Data.

- What is the flow of props?
    - One Way Down, from Parent to Child.

<br>

## Things I want to know more about

<br>

- What other kind of props can we use with React.
