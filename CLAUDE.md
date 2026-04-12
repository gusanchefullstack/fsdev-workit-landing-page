# Guidelines
0. Create a plan for the project and allow me to validate it. 
1. Implement the project using HTML/CSS classes only and Javascript if needed. Don't use any other external library.
2. Follow the style guidelines defined in @style-guide.md.
3. Create a README.md based in README-template.md once the project is finished
4. Use the content of the body in @index.html as source text
5. Use the @data.json as source of data for info displayed.
6. Consider the figma-design file called results-summary-component.fig as source or truth for design, styling, fonts. Use the images contained in this file like svgs.
7. The screenshots inside @design folder reflect the expected output for the several screens: mobile, desktop. Infer the best responsive design for tablet.
8. Initialize local git repo. Only with my approval create a repo in github. Avoid that figma designs be pushed to github (with .gitignore file).
9. Split the implementation tasks/parts of the project in separated commits .
10. Update the Author section in README with the following contact info. Add icons to each related link address.
    https://www.linkedin.com/in/gustavosanchezgalarza/
    https://github.com/gusanchefullstack
    https://hashnode.com/@gusanchedev
    https://x.com/gusanchedev
    https://bsky.app/profile/gusanchedev.bsky.social
    https://www.freecodecamp.org/gusanchedev
    https://www.frontendmentor.io/profile/gusanchefullstack
11. Use playwright skills to test implementation at 375px and 1440px screens. Take screenshots for both scenarios and add them to the readme in the screenshots section.


# Architecture
1. Implement the project using HTML/CSS and Javascript if needed.
2. Use vite as deploying server for frontend
3. The source code should be in src/ folder under the project root.
4. Colors, gradients, typography should be parameterized in the project to allow further changes.