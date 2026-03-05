# BrainGlobe: Miscellaneous maintenance work on BrainGlobe overall infrastructure (Varun Singh)

## Personal details

- **Full name**: Varun Singh

- **Email**: varun.singh10011@gmail.com
- **GitHub username**: AlgoFoe
- **Zulip username**: Varun Singh
- **Location & time-zone**: India, GMT+5:30 (Asia/Kolkata)
- **Personal website / project portfolio**: https://github.com/AlgoFoe

#### **Code contribution**

<table>
    <thead>
        <tr>
            <th>S.No</th>
            <th>Description</th>
            <th>Issue</th>
            <th>PR/Link</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>Refactored NiftyReg cmd execution to use argument lists instead of shell strings, improving robustness and handling of paths with spaces across platforms.</td>
            <td><a href="https://github.com/brainglobe/brainreg/issues/4">#4</a></td>
            <td><a href="https://github.com/brainglobe/brainreg/pull/267">#267</a></td>
        </tr>
        <tr>
            <td>2</td>
            <td>Added an early check in atlas generation to detect existing output directories and introduced an explicit overwrite option to prevent late-stage failures.</td>
            <td><a href="https://github.com/brainglobe/brainglobe-atlasapi/issues/731">#731</a></td>
            <td><a href="https://github.com/brainglobe/brainglobe-atlasapi/pull/733">#733</a></td>
        </tr>
        <tr>
            <td>3</td>
            <td>Fixed misalignment of cellfinder points when using anisotropic voxel sizes by ensuring created points inherit the image scale.</td>
            <td><a href="https://github.com/brainglobe/cellfinder/issues/571">#571</a></td>
            <td><a href="https://github.com/brainglobe/cellfinder/pull/572">#572</a></td>
        </tr>
        <tr>
            <td>4</td>
            <td>Consolidated docs dependencies into pyproject.toml as an optional docs extra.</td>
            <td><a href="https://github.com/neuroinformatics-unit/ethology/issues/127">#127</a></td>
            <td><a href="https://github.com/neuroinformatics-unit/ethology/pull/131">#131</a></td>
        </tr>
        <tr>
            <td>5</td>
            <td>Updated packaging configuration to resolve deprecated license syntax and align build and pre-commit tooling with current standards.</td>
            <td><a href="https://github.com/neuroinformatics-unit/python-cookiecutter/issues/160">#160</a></td>
            <td><a href="https://github.com/neuroinformatics-unit/python-cookiecutter/pull/161">#161</a></td>
        </tr>
        <tr>
            <td>6</td>
            <td>Moved long-running tasks to a threaded worker to enable Activity Dock progress feedback.</td>
            <td><a href="https://github.com/brainglobe/brainglobe-stitch/issues/39">#39</a></td>
            <td><a href="https://github.com/brainglobe/brainglobe-stitch/pull/62">#62</a></td>
        </tr>
    </tbody>
</table>

## Project Proposal

- **Synopsis**

  This project focuses on improving and modernising BrainGlobe's overall infrastructure. The work will involve simplifying and exposing a cleaner meta-package API, standardising function signatures and terminology across repositories, improving CI workflows, automating API documentation creation, and refining the packaging and release process. The aim is to make the ecosystem easier to manage going forward.

- **Project size**<br>
  Large

- **Why is the project important?**

  As BrainGlobe continues to grow, both in terms of features and the number of repositories, maintaining consistency across the ecosystem becomes more challenging. I have noticed that differences in API structure, argument conventions, CI setups, packaging workflows, and documentation standards can gradually introduce friction into development. Over time, this can slow down contributions and complicate reviews, especially in a large and distributed codebase. <br>
  Improving and standardising the infrastructure across repositories would make the ecosystem more predictable and easier to work with for both users and contributors. By focusing on maintainability at the ecosystem level rather than enhancing a single tool, this project aims to strengthen the foundation of BrainGlobe and ensure it remains scalable, modern, and sustainable as it continues to evolve.

- **Goals**

    - Expose simplified and consistent APIs from individual tools at the BrainGlobe meta-package level.
    - Standardise terminology across repositories and functions.
    - Standardise the use of positional and keyword arguments across repositories.
    - Automate the generation and publishing of API reference documentation on the BrainGlobe website.
    - Replace tox with uv across BrainGlobe's CI workflows via GitHub Actions.
    - Improve and modernise the conda-forge release process, including:
      - Adding setuptools where required
      - Migrating to conda-forge v1 recipe support
    - Standardise repository badges and project metadata for consistency.


**Implementation timeline**

**Deliverables**

- Simplify the BrainGlobe meta-package API and standardise terminology and function argument conventions across repositories.
- Migrate CI workflows from tox to uv.
- Improve conda-forge packaging and release configuration.
- Set up automated API documentation generation.

**Stretch Goals**

- Lazy-load meta-package imports to reduce startup time.
- Create a small developer guide documenting API conventions and packaging standards for future contributors. 
- Improve cross-repository automated checks for consistent standards.

**Weekly timeline**

<table>
    <thead>
        <tr>
            <th>Timeline</th>
            <th>Deliverables</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong>Community Bonding Period <br> (May 1 - May 24)</strong></td>
            <td>
                <ul>
                    <li>Take feedback on existing PRs to get them merged.</li>
                    <li>Audit repositories for API exposure, terminology inconsistencies and packaging setup.</li>
                    <li>Discuss implementation plan with the mentor(s) and define which APIs should be exposed at meta-package level.</li>
                    <li>Finalise the project implementation details with the mentor(s) for cross-repository changes.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Week 1-2 <br> (May 25 - June 7)</strong></td>
            <td>
                <ul>
                    <li>Refactor brainglobe/__init__.py to expose selected APIs.</li>
                    <li>Implement first set of API re-exports from core packages.</li>
                    <li>Design consistent public API interface.</li>
                    <li>Add initial unit tests validating imports and API exposure.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Week 3-4 <br> (June 8 - June 21)</strong></td>
            <td>
                <ul>
                    <li>Check BrainGlobe repositories for inconsistent terms and create a standard naming guideline for common parameters across tools.</li>
                    <li>Update function and parameter names to follow consistent naming conventions across the codebase.</li>
                    <li>Standardise positional parameter order and naming across repositories while maintaining backward compatibility.</li>
                    <li>Add unit tests verifying that updated APIs.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Week 5-6 <br> (June 22 - July 5)</strong></td>
            <td>
                <ul>
                    <li>Apply the defined naming and parameter conventions across the remaining repositories and modules.</li>
                    <li>Update docstrings, parameter descriptions, and usage examples to reflect the new standardised APIs. </li>
                    <li>Run full test suites to ensure no issues are introduced and document the API changes.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Week 7-8 <br> (July 6 - July 19)</strong></td>
            <td>
                <ul>
                    <li>Replace tox with uv-based environments in CI workflows and update dependency installation steps.</li>
                    <li>Modify gh-actions workflow files to use uv for environment creation and running tests.</li>
                    <li>Update configuration files where required for compatibility with the new setup.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Week 9-10 <br> (July 20 - August 2)</strong></td>
            <td>
                <ul>
                    <li>Update  conda-forge feedstock recipes to follow consistent build configurations.</li>
                    <li>Add missing build dependencies such as setuptools where required.</li>
                    <li>Begin migration of recipes to conda-forge v1 format.</li>
                    <li>Document the updated packaging and release process for maintainers.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Week 11-12 <br> (August 3 - August 16)</strong></td>
            <td>
                <ul>
                    <li>Set up Sphinx autodoc for automated API documentation.</li>
                    <li>Standardise repository badges and documentation across repositories, along with any remaining bug fixes and additional tests.</li>
                    <li>Prepare and submit the final project report.</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

- **Communication Plan** 

  I plan to communicate with my mentors on GitHub and Zulip Chat and have weekly meetings to discuss the progress and blockers if any. 

## Personal Statement

- **Past Experience**
    
  I have been programming for a little over three years now, starting from my first year of college, mainly working with C++, Python, and web technologies. During this time, I have also completed three SDE internships, including at KaleidoXP, where I worked on a medical imaging platform using Python(Django), computer vision, and full-stack development that was deployed across hospitals. One project I am particularly proud of is [Hackpack CLI](https://www.npmjs.com/package/hackpack-cli), an open-source npm package I built to scaffold full-stack hackathon projects quickly, which has reached around 4000 total downloads. Building and maintaining it has given me hands-on experience creating developer tools and supporting real users in the open-source community

- **Projects**
    - [Full-Stack Project Scaffolding CLI](https://github.com/YashVerma-code/hackpack)
    - [Lightweight Embedded DB Engine](https://github.com/AlgoFoe/tinyh2)
    - [AI‑Powered Chat App](https://github.com/AlgoFoe/ai-yo)
        

- **Motivation**
    
  I am motivated to work on this project because it focuses on improving the core infrastructure of the entire BrainGlobe ecosystem rather than adding features to a single tool. From recent discussions, it is clear that maintainability and consistency across repositories are important priorities as the project continues to grow. Working on API standardisation, CI modernisation, packaging, and documentation automation aligns strongly with my interest in writing clean and scalable code. <br>
  What excites me most is the long-term impact. Strengthening the ecosystem's foundations will reduce development friction and benefit both current and future contributors. As a student, the opportunity to contribute at this architectural level in an established open-source project is both challenging and extremely valuable for my growth as a developer.

- **Match**

  I believe I am a good fit for this project because I already have experience working with Python, developer tooling, and open-source projects. Through my internships and my Hackpack CLI open-source package, I have worked on real-world codebases and tools used by others. I am also actively contributing to the BrainGlobe ecosystem, which has helped me understand the repositories and development workflow. I am someone who puts in a lot of effort and always tries to give my best, and I am committed to improving the maintainability of the project.

- **Availability**

  I will be on summer break from university and available from 8th May to 31st August. During this period, I can commit approximately 30–35 hours per week to the project, with an additional 2 hours on weekdays if needed.

## GSoC

- **GSoC Experience**

  Through GSoC, I hope to learn what it's like to work closely with maintainers on a real open-source project and understand how large projects are designed and maintained. I am also looking forward to improving my skills while contributing something meaningful that benefits the community.

- **Are you also applying to projects with other organisations in GSoC 2026?**

  No, this is the only organisation I am applying to.

## Future contributions

- **After GSoC**

  I would definitely like to continue contributing to BrainGlobe and other NIU post GSoC. I am planning to pursue a master's degree next year, so I expect to remain in academia and research-related environments for the next few years.

- **Further ideas**

  If given the time and resources, I would love to help improve the user and developer experience across repositories. This could include adding progress indicators to multiple interfaces, building a unified CLI for easier tool access, and creating dev containers and walkthroughs to make onboarding smoother for new contributors.
