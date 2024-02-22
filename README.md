# Render

Il termine "rendering" si riferisce al processo di conversione di componenti React in elementi visuali sullo schermo, che avviene tramite il metodo ReactDOM.render() o tramite il render del componente principale all'interno dell'applicazione. Il rendering è un concetto fondamentale in React e comprende diverse modalità di utilizzo.

## Rendering Condizionale

Il rendering condizionale in React si riferisce alla pratica di mostrare o nascondere determinati elementi o componenti in base a condizioni specifiche. Questo viene spesso eseguito utilizzando costrutti come **if, else, ternary operator, e logical && operator** all'interno della struttura JSX. 


    function App() {
    const isLoggedIn = true;

    return (
        <div>
        {isLoggedIn ? <UserGreeting /> : <GuestGreeting />}
        </div>
    );
    }

In questo esempio, a seconda del valore della variabile isLoggedIn, viene mostrato il componente UserGreeting se l'utente è autenticato, altrimenti viene mostrato il componente GuestGreeting.

### Rendering condizionale basato su stato

Il metodo di rendering condizionale basato su stato in React consente di controllare la resa di un componente in base allo stato di una variabile o di una prop. In questo modo, è possibile decidere se un componente deve essere visualizzato o meno sulla base di condizioni dinamiche.

    function Card({ title, description, isVisited, imgURL, children }) {
    if (isVisited) {
        return null;
    }
    
    return (
        <div className="rounded-md bg-gradient-to-br to-sky-950 from-slate-950">
        <img src={imgURL} alt="" className="h-[300px] w-[300px]" />
        <div className="flex flex-col p-4">
            <h2 className="text-2xl">{title}</h2>
            <p className="text-gray-500">{description || children}</p>
            <span>❌ non visitata</span>
        </div>
        </div>
    );
    }

    export default Card;

Nel componente Card, viene utilizzato un metodo di rendering condizionale per determinare se il componente deve essere visualizzato o se deve essere nascosto in base al valore della prop isVisited. Se isVisited è true, il componente non viene visualizzato e viene restituito null. Altrimenti, se isVisited è false, il componente viene mostrato normalmente.

### Rendering condizionale con operatore ternario

Il metodo di rendering condizionale con operatore ternario in React consente di determinare quale componente o elemento renderizzare in base a una condizione booleana. Utilizzando l'operatore ternario, è possibile eseguire una valutazione condizionale in linea e restituire un elemento o un altro a seconda del risultato della condizione.

    function Card({ title, description, isVisited, imgURL, children }) {
    return (
        <div className="rounded-md bg-gradient-to-br to-sky-950 from-slate-950">
        <img src={imgURL} alt="" className="h-[300px] w-[300px]" />
        <div className="flex flex-col p-4">
            <h2 className="text-2xl">{title}</h2>
            {isVisited ? <span>✔️ visitata</span> : <span>❌ non visitata</span>}
        </div>
        </div>
    );
    }

    export default Card;

Nel componente Card, viene utilizzato l'operatore ternario per determinare se visualizzare un messaggio che indica se la card è stata visitata o meno. Se isVisited è true, viene visualizzato il messaggio "✔️ visitata", altrimenti viene visualizzato il messaggio "❌ non visitata".

### Rendering condizionale con operatore AND

Il metodo di rendering condizionale con l'operatore AND in React consente di renderizzare un componente o un elemento solo se una determinata condizione è vera. 

    function Card({ title, description, isVisited, imgURL, children }) {
    return (
        <div className="rounded-md bg-gradient-to-br to-sky-950 from-slate-950">
        <img src={imgURL} alt="" className="h-[300px] w-[300px]" />
        <div className="flex flex-col p-4">
            <h2 className="text-2xl">{title}</h2>
            {isVisited && <span>✔️ visitata</span>}
        </div>
        </div>
    );
    }

    export default Card;

Nel componente Card, l'operatore AND && viene utilizzato per renderizzare il messaggio "✔️ visitata" solo se isVisited è true.

### Rendering condizionale con isAdmin

Il rendering condizionale con isAdmin in React consente di renderizzare un componente o un elemento solo se l'utente è un amministratore o ha i privilegi necessari. Questo approccio è utile quando si desidera mostrare determinati elementi solo agli utenti autorizzati, come ad esempio i pulsanti per eliminare o modificare contenuti.

    function Card({ title, description, isVisited, imgURL, isAdmin, children }) {
    const visitedLabel = isVisited ? "✔️ visitata" : "❌ non visitata" 
    return (
        <div className="rounded-md bg-gradient-to-br to-sky-950 from-slate-950">
        <img src={imgURL} alt="" className="h-[300px] w-[300px]" />
        <div className="flex flex-col p-4">
            <h2 className="text-2xl">{title}</h2>
            <span>{visitedLabel}</span>
            {isAdmin && <span>❌ rimuovi città</span>}
        </div>
        </div>
    );
    }

    export default Card;

Nel componente Card, la prop isAdmin viene utilizzata per condizionare il rendering del messaggio "❌ rimuovi città". Se l'utente è un amministratore (isAdmin è true), il messaggio verrà visualizzato e il componente <span> verrà renderizzato. Altrimenti, se l'utente non è un amministratore (isAdmin è false), il messaggio non verrà mostrato e il componente <span> non verrà renderizzato.

## Rendering di Liste:

Il rendering di liste in React viene utilizzato per mostrare un insieme dinamico di elementi, spesso ottenuti da un array di dati. Questo viene generalmente eseguito utilizzando il metodo map() su un array di dati all'interno della struttura JSX. Ad esempio:


    function App() {
    const numbers = [1, 2, 3, 4, 5];

    return (
        <ul>
        {numbers.map((number) => (
            <li key={number}>{number}</li>
        ))}
        </ul>
    );
    }

In questo esempio, la funzione map() viene utilizzata per iterare su ogni elemento dell'array numbers, e per ciascun elemento viene restituito un elemento <li> contenente il numero corrispondente.
