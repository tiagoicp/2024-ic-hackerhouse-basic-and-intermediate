# Basic and Intermediate Challenge for ICP AI HackerHouse

Welcome to this tutorial that is for people to get started into ICP, a decentralized cloud built on blockchain technology. Architected for being general purpose, the only limit you have is your imagination. 🙂🚀

On this challenge, the main goals are:

- to introduce to IC, showcasing great examples of what is already possible
- to help you getting started in a quick but still effective way
- to hopefully convince you the IC stack and ecosystem is a great place to have a Dev career or co-found a startup.

## Challenge Overview

This challenge will be in Motoko. We have prepared a Codespace for you, so you don't waste time on local setup and can go directly to the fun part, coding! ⌨️

In the basic challenge you will:
- Develop a canister (backend) that logs in with Gmail, with an ICP wallet provider called NFID.
- Work on the backend, understanding data structures, packages, stable/dynamic memory, etc.
- You will allow to setup a user profile and safely store user records (like the results of the AI Model).

In the intermediate challenge you will:
- Connect that backend to the API of HuggingFace, using IC HTTP Outcalls.
- We will use a basic one, phrase sentiment analysis model.
- You will need to parse the response and more clearly show the model result.
- Then on the frontend you need to improve it and allow the user to interact with the new AI / API features you just added.

## Submission Details & Requirements

For getting the 50 (only basic) or the 100 (basic + intermediate) ckUSDT prize, you will need to:
- Join the Taikai platform (where we publickly handle all the submissions): https://taikai.network/icp-portugal/hackathons/ICP-AI-HACKERHOUSE
- Create a project, following the instructions on the video, namely:
  - Title saying "Easy Challenge - Your Name" or "Intermediate Challenge" if it's the case.
  - Add your github that allows to see the code finishing the challenge.
  - A video recording of the Candid UI (Basic Challenge) or the Frontend (Intermediate Challenge) showing the dApp behaving as expected on the challenge.

## Tutorial Videos

Tutorial Videos explaining and walking through each of the methods / behaviour expected. 
Note: Feel free to listen at 1.2x speed 😛

IC Overview (recorded on a recent workshop with CS Students):
- https://www.youtube.com/watch?v=wyHAh9i1cFI

Basic:
- Github and Codespace setup
- Overview of code structure
- Login and user registration / update
- Store more complex data, like previous model results associated with an User.

Intermediate:
- HTTP Outcall and Hugging Face API overview
- Call and parse the data, and select best result
- Render and improve frontend to enable user to better interact with the features you built.



# General Instructions of `dfx new`

Welcome to your new `hackerhouse_basic` project and to the Internet Computer development community. By default, creating a new project adds this README and some template files to your project directory. You can edit these template files to customize your project and to include your own code to speed up the development cycle.

To get started, you might want to explore the project directory structure and the default configuration file. Working with this project in your development environment will not affect any production deployment or identity tokens.

To learn more before you start working with `hackerhouse_basic`, see the following documentation available online:

- [Quick Start](https://internetcomputer.org/docs/current/developer-docs/setup/deploy-locally)
- [SDK Developer Tools](https://internetcomputer.org/docs/current/developer-docs/setup/install)
- [Motoko Programming Language Guide](https://internetcomputer.org/docs/current/motoko/main/motoko)
- [Motoko Language Quick Reference](https://internetcomputer.org/docs/current/motoko/main/language-manual)

If you want to start working on your project right away, you might want to try the following commands:

```bash
cd hackerhouse_basic/
dfx help
dfx canister --help
```

## Running the project locally

If you want to test your project locally, you can use the following commands:

```bash
# On a new tab start the replica, it will be important for logs
dfx start

# On previous tab, deploy your canisters to the replica and generate your candid interface
dfx deploy
```

Once the job completes, your application will be available at `http://localhost:4943?canisterId={asset_canister_id}`.

If you have made changes to your backend canister, you can generate a new candid interface with

```bash
npm run generate
```

at any time. This is recommended before starting the frontend development server, and will be run automatically any time you run `dfx deploy`.

If you are making frontend changes, you can start a development server with

```bash
npm start
```

Which will start a server at `http://localhost:8080`, proxying API requests to the replica at port 4943.

### Note on frontend environment variables

If you are hosting frontend code somewhere without using DFX, you may need to make one of the following adjustments to ensure your project does not fetch the root key in production:

- set`DFX_NETWORK` to `ic` if you are using Webpack
- use your own preferred method to replace `process.env.DFX_NETWORK` in the autogenerated declarations
  - Setting `canisters -> {asset_canister_id} -> declarations -> env_override to a string` in `dfx.json` will replace `process.env.DFX_NETWORK` with the string in the autogenerated declarations
- Write your own `createActor` constructor
