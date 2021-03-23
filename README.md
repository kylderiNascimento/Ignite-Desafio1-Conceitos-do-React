
![Captura de Tela 2021-03-22 às 21 38 52](https://user-images.githubusercontent.com/49724512/112075330-0e1b0700-8b57-11eb-9e81-e383edc3fe8f.png)

Link do desafio: https://www.notion.so/Desafio-01-Conceitos-do-React-51e4099a6e2f4d4bae94f9fe75bb769d

## O que devo resolver na aplicação?

Com o template já clonado, as depêndencias instaladas, você deve completar onde não possui código com o código para atingir os objetivos de cada teste. Nesse desafio, você deve editar apenas o seguinte arquivo para completar as funcionalidades da aplicação:

- [src/components/TaskList.tsx;](https://github.com/rocketseat-education/ignite-template-reactjs-conceitos-do-react/blob/main/src/components/TaskList.tsx)

### components/TaskList.tsx

Esse é o componente responsável por todas as funcionalidades da aplicação, é um componente simples, mas onde botaremos em prática várias partes da manipulação do estado.

Você deve criar as funcionalidades para as três funções presentes nesse arquivo, que são:

- **handleCreateNewTask**: Deve ser possível adicionar uma nova task no estado de `tasks`, com os campos `id` que deve ser gerado de forma aleatória, `title` que deve ser um texto e `isComplete` que deve iniciar como false.
- **handleToggleTaskCompletion:** Deve alterar o status de `isComplete` para uma task com um ID específico que é recebido por parâmetro.
- **handleRemoveTask:** Deve receber um ID por parâmetro e remover a task que contém esse ID do estado.

## Resolução

Sabendo que:
```jsx
interface Task {
  id: number;
  title: string;
  isComplete: boolean;
}

const [tasks, setTasks] = useState<Task[]>([]);
const [newTaskTitle, setNewTaskTitle] = useState('');
```

RESOLVIDO: **handleCreateNewTask**

```jsx
function handleCreateNewTask() {
    // Crie uma nova task com um id random, não permita criar caso o título seja vazio.

    // Verificando se o input está vazio
    if (!newTaskTitle){
      console.log('Campo vazio.');
      return;
    }

    const newTask = {
      id: Math.random(),
      title: newTaskTitle,
      isComplete: false
    }

    setTasks(tasks => [...tasks, newTask]);

    // Limpando o input
    setNewTaskTitle('');

  }
```

RESOLVIDO: **handleToggleTaskCompletion**

```jsx
function handleToggleTaskCompletion(id: number) {
    // Altere entre `true` ou `false` o campo `isComplete` de uma task com dado ID

    // Vamos mapear o array e atualizar o isComplete
    const updateTask = tasks.map(task => task.id == id ? {
        // Vamos atualizar a informacao segundo o check
        ...task, isComplete: !task.isComplete
    } : task);

    setTasks(updateTask);

  }
```

RESOLVIDO: **handleRemoveTask**

```jsx
function handleRemoveTask(id: number) {
    // Remova uma task da listagem pelo ID

    // Trazer todos diferente do task passado
    const newListTask = tasks.filter(task => task.id != id);

    setTasks(newListTask);

  }
```

# Solução do desafio

Gravei um passo a passo da resolução desse desafio.

https://youtu.be/KjPh6Rm1zwk?list=PLjm0b1mZwR0fZcmlIlajFGliSqyPk8lmN
