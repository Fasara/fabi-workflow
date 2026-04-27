# GitHub Actions workflow: description and local testing

This workflow runs on every `push` to the repository and executes a single job that checks out the code, runs a composite action to "greet" someone, and then prints the output produced by that action.

### Key parts:
- **Trigger**
  - `on push` - any push to any branch will start the workflow.
 
- **Jobs**
  - One job: `hello_world_job`
  - Runs on: `ubintu-latest`
  - Displays name: "Just a job to say hello."


- **Steps**
  
  i. `actions/checkout@v3` - checks out the repository so subsequent steps can access the code.

  ii. Runs a composite action `Fasara/composite-action-example@main` with:
    - step id: `pippo`
    - input `who-to-greet: "Fabiana"` This action is expected to perform some greeting and expose outputs
 
  iii. Echoes an output from the composite action:
    - `echo random-number ${{ steps.pippo.outputs.random-number }}` This prints the random-number output value produced by the pippo step to the workflow logs.

  
