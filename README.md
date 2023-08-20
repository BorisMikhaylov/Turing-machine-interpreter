# Turing-Machine-Interpreter

### Boris Mikhaylov

#### Subtasks 3 and 4 (parser and interpreter)

[parser and interpreter](https://github.com/ilma4/fl-2022-hse-win/tree/proj/Parser)

### Ilya Malahov

#### Subtask 1 (syntax description)

[Description](https://github.com/ilma4/fl-2022-hse-win/blob/67821c966dab0677f52675cecfe093e6fdf69865/Description/description.md)


#### Subtask 2 (IDE support)

[Description + launch instruction](https://github.com/ilma4/fl-2022-hse-win/blob/d053b665ea8128e19ebddb4454086aefcf9374a1/VSCode-extension/README.md)

## Summary


### Boris Mikhaylov

Done:

* Parser: The parser module can read and interpret Turing Machine descriptions written in a custom format. It extracts information about the machine's states, alphabet, transition rules, and initial configuration.
* Interpreter: The interpreter module simulates the execution of a given Turing Machine on a specific input. It follows the transition rules defined in the description and showcases step-by-step execution, aiding in visualizing the computation process.
* Interactive Interface: Users can input the Turing Machine description and initial input through an interactive command-line interface. The interpreter then provides a detailed output, showing the state transitions and tape modifications at each step.
* Error Handling: The interpreter includes comprehensive error handling, notifying users of issues such as invalid machine descriptions, missing transition rules, or invalid input.

### Ilya Malahov

Done:

* Invented and described a grammar to describe Turing Machines.
* Described this grammar in the format [TextMate](https://macromates.com/manual/en/language_grammars) for syntax highlighting in VSCode.
* Implemented a language server, with auto-completion and code verification functions.
* Used Boris's parser in the server to get identifiers (used in auto-completion) and errors in the code.

Implementation process:

Studied the requirements of the main development environments for the new language support plugin. Chose Visual Studio Code because of its simplicity and useful [examples](https://github.com/microsoft/vscode-extension-samples). I studied the structure and principle of operation of the Turing Machine, came up with an easy-to-parse grammar that allows you to do correct syntax highlighting without LST. Described this grammar in TextMate format for highlighting in VSCode. Implemented a simple language server that uses Boris's parser for code completion and verification.

Difficulties:

The main difficulty was in understanding exactly how to do it. I found guides about how to make this or that function in isolation from each other, but not all at once. But when I collected enough information, I combined several examples into one project and remade it to suit my tasks and grammar. There were also problems with the `npm` package manager (hanging), vpn solved the problem.
