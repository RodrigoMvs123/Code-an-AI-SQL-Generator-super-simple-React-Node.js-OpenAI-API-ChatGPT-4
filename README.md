# Code-an-AI-SQL-Generator-super-simple-React-Node.js-OpenAI-API-ChatGPT-4

https://www.youtube.com/watch?v=mb36Ny-VNgU

https://raw.githubusercontent.com/RodrigoMvs123/Code-an-AI-SQL-Generator-super-simple-React-Node.js-OpenAI-API-ChatGPT-4/main/README.md

https://www.brydge.dev/

https://openai.com/product

TypeScript SQL Generator 

Terminal 

aniakubow@Anias-Mac-Book-Pro ~% cd WebstormProjects
aniakubow@Anias-Mac-Book-Pro WebstormProjects % npx create-react-app my-app - - template typescript 

Components 
CodeDisplay.tsx
interface CodeDisplayProps{
       text: string
}

const CodeDisplay = ({ text }) => {
      return (
         <div className=”code-display”>
               <div className=”buttons”>
                  <div className=”button first”></div>
                  <div className=”button middle”></div>
                  <div className=”button last”></div>

             </div>
           <div className=”code-output”>
                  <p>{text}</p>
           </div>
         </div>
     )
} 

export default CodeDisplay

MessageDisplay.tsx

interface UserMessage {
      role: string, 
      content: string
} 

interface MessageDisplayProps {
        message: userMessage
}

const MessageDisplay = ({ message }: MessageDisplayProps) => {
      return (
         <div className=”message-display”>
              <p id=”icon”>⊚</p>
              {/*<p>{message.role}</p>*/}
              <p>{message.content}</p>
         </div>
     )
} 

export default MessageDisplay


compart.com/en/unicode/U+229A


MessagesDisplay.tsx
import MessageDisplay from “./MessageDisplay”

interface UserMessage {
      role: string, 
      content: string
} 

interface MessagesDisplayProps {
      userMessages: UserMessage[]
}

const MessagesDisplay = ({ userMessages }: MessagesDisplayProps) => {
      return (
         <div className=”messages-display”>
              {user.Messages.map((userMessage, _index) => 
                     <MessageDisplay key={_index} message={userMessage}/>)}
         </div>
     )
} 

export default MessagesDisplay


App.tsx
import { useState } from “react”
import MessagesDisplay from “/.components/MessagesDisplay”
import CodeDispay from “./components/CodeDisplay”

interface ChatData {
       role: string,
       content: string,
}

const App = () => {
      const [value, setValue ] = useState<string>(“”)
      const [ chat, setChat ] = useState<ChatData[]>([]) 

      const getQuery = async () => {
      try {
      const options: RequestInit = {
             method: “POST”, 
             headers: {
                     “Content-Type”: “application/json”
},
             body: JSON.stringify({
                     message: value
   })
}


       const response =  await  fetch(“https://localhost:8000/completions”, options)
       const data = await response.json()
       console.log(data)
       const userMessage = {
              role: “user”, 
              content: value
}
       set.Chat(oldChat  => [...oldChat, data, userMessage])
      } catch (error) {
           console.error(error)
      }
}

const clearChat = () => {
        setValue(“”)
        setChat([])
}


const filteredUserMessages = chat.filter(message => message.role === “user”)
const latestCode = chat.filter(message => message.role === “assistant”).pop()

      return (
         <div className=”app”>
             <MessagesDisplay userMessages={filteredUserMessages}/>
             <input value={value} onChange={e => setValue(e.target.value)}/>
             <CodeDisplay text={latestCode?.content || “”}/>
             <div className=”button-container”>
                 <button id=”get-query” onClick={getQuery}>Get Query!<button/>
                 <button id=”clear-chat” onClick={clearChat}>Clear Chat<button/>             
             <div/>
         </div>
     )
} 

export default App

index.css
* {
      font-family: Verdana, Tahoma, sans-serif;
      color: rgb(34, 34, 34);
}

body {
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: rgb(250, 250, 250);
}

p, input {
      font-size:16px;
}

.app {
       height: 80vh;
       width: 80vw;
       background-color: rgb(255, 255, 255);
       border-radius: 10px;
       box-shadow: rgba(0, 0, 0, 0.16) 0, 1px 4px;
       display: flex;
       justify-content: center;
       flex-direction: column;
}

.code-display {
       width: 96%;
       margin: 2%;
       height: 46%;
       border-radius: 8px;
       background-color: rgb(34, 34, 34);
       overflow: hidden;
}

.code-output {
       margin: 20px;
}

.code-output p {
       color: rgb(255, 189, 45);
}


.buttons {
       width: 100%;
       height: 35px; 
       background-color: rgb(50, 50, 50);
       display: flex; 
       align-items: center;
       padding-left: 5px;
}

.button {
       height: 15px;
       width: 15px;
       border-radius: 50%;
       margin: 4px;
       background-color: red;
}

.button.first {
       background-color: rbg(255, 96, 86);
}

.button.middle {
       background-color: rbg(255, 189, 45);
}

.button.last {
       background-color: rbg(38, 201, 64);
}

.messages-display {
       width: 96%;
       margin: 2%;
       height: 46%;
       overflow-y: scroll;
}

::-webkit-scrollbar {
       -webkit-appearance: none;
       width: 7px;
}

::-webkit-scrollbar-thumb {
       border-radius: 4px; 
       background-color: rgb(0, 0, 0, 5);
       -webkit-box-shadow: 0 0 1px rgba(255, 255, 255, .5);
}

.message-display {
       width: 100%;
       display: flex;
       border-radius: 5px;
       box-sizing: border-box;
       background-color: rgb(250, 250, 250);
       margin: 5px 0; 
}

p#icon {
       padding: 0 7px;
}

input {
       margin: 2%;
       padding: 16px;
       border: solid rgba(0, 0, 0, 0.16) 1px;
       box-sizing: border-box;
       border-radius: 5px;
}

.button-container {
       margin: 2%;
       display: flex;
       justify-content: flex-end;
}

.button-container button {
       text-transform: uppercase;
       padding: 7px;
       border: none;
}

button#get-query {
       border-radius: 10px 0 0 10px;
       background-color: rgb(255, 95, 86); 
}


button#clear-chat {
       border-radius: 0 10px 10px 0;
       background-color: rgb(255, 189, 45); 
}




index.tsx
import React from ‘react’
import ReactDOM from ‘react-dom/client’
import ‘./index.css’
import App from ‘./App’

const root = ReactDOM.createRoot (
      document.getElementById(‘root’) as HTMLElement
)
root.render(
    <React.StrictMode>
         <app/>
    </React.StrictMode
)



package.json 
“type”:”module”

“scripts”: {
“start:frontend”: “react-scripts start”,
“start:backend”: “ts-node - - esm index.ts”,
},

Terminal 
aniakubow@Anias-Mac-Book-Pro typescript-sql-generator % npm i ts-node
aniakubow@Anias-Mac-Book-Pro typescript-sql-generator % npm i cors express

aniakubow@Anias-Mac-Book-Pro typescript-sql-generator % npm run start:frontend
localhost:3000

aniakubow@Anias-Mac-Book-Pro typescript-sql-generator % npm i openai

index.ts
import express , { Application, Request, Response } from “express”
import cors from “cors”
import { Configuration, OpenAIApi } from “openai”
import * as dotenv from “dotenv”
dotenv.config()
const PORT: number = 8000 

const app: Application = express()
app.use(cors())
app.use(express.json())


const API_KEY: string = process.env.API_KEY

const configuration = new Configuration ({
       apiKey: API_KEY
})

const openai = new OpenAIApi(configuration)

app.post(“/completions”, async (req: Resquest, res: Response) => {
      try {
          const completion = await openai.createChatCompletion({
              model: “gpt-4”, 
              messages: [
                           {
                                   role: “user”,
                                   content: “Create a SQL request tp ” + req.body.message
                            }
                            ]
})
res.send(completion.data.choices[0].message)
    } catch (error) {
         console.error(error)
         res.status(500).send(“Server error”)
    }  
})


app.listen(PORT, () => console.log(‘Your server is running on PORT ${PORT}’))

aniakubow@Anias-Mac-Book-Pro typescript-sql-generator % npm i - - save - dev.@types/cors


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


aniakubow@Anias-Mac-Book-Pro typescript-sql-generator % npm run start:backend

aniakubow@Anias-Mac-Book-Pro typescript-sql-generator % npm i dotenv 

.env
API_KEY=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

