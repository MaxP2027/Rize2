This workflow runs two ways, when someone pushes to main and when someone opens a pull request intco main. So basically any change headed towards main will set it off.

There's four steps in the process which are  checkout code, validate HTML, check links, and upload artifact. Deploy job runs after that, but only once those four are done.

Checkout code pulls your files onto the machine, since GitHub Actions starts with a totally empty machine every time. Without this step there'd be nothing for the other steps to even work with.

The environment part tells GitHub this job is deploying to the github-pages environment and grabs the live url once its done. It also ties into them permissions above it, since Pages deployment need that specific access to work.

Auto deployment is more rdeliable cause it does the same steps the same way every single time, it dont forget to check links or skip anythung by accident. It also stops broken code from going live since deploy won't run unless build-and-test passes first.

If you pushed to a different branch nothing would happen at all, since the workflow only listen for main. That's why your PR runs from those feature branches only ran build-and-test and never actually deployed.