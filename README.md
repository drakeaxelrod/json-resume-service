<div align="center">
  <img width="100%" height="60" src="public/jaas.svg" />
  <div><samp><b>JSONResume as a Service</b></samp></div>
  <div><a href="https://json-resume-service.vercel.app/"><sup><samp>json-resume-service.vercel.app</samp></sup></a></div>
    <a href="#what"><samp><b>What</b></samp></a>
  ▪️<a href="#why"><samp><b>Why</b></samp></a>
  ▪️<a href="#how"><samp><b>How</b></samp></a>
  ▪️<a href="#usage"><samp><b>Usage</b></samp></a>
</div>

---

<div align="center">
  <table>
    <tr>
      <td>
        <div>🔸<a href="#development"><sub><sup><b>Development</b></sup></sub></a></div>
        <div>🔹<a href="#contributors"><sub><sup><b>Contributors</b></sup></sub></a></div>
        <div>▫️<a href="#license"><sub><sup><b>License</b></sup></sub></a></div>
      </td>
      <td align="center" width="30%">
        <img height="24" width="24" src="public/icon.png" alt="icon" />
        <a href="https://vercel.com/new/clone?repository-url=https//github.com/DrakeAxelrod/json-resume-service">
          <img src="https://vercel.com/button" width="70" title="Deploy with Vercel" />
        </a>
      </td>
    </tr>
  </table>
</div>


---

<div align="center">
  <img src="public/resume-service-image.png" alt="resume service example" />
</div>

---

## What

Serverless service to generate dynamic resumes from **remote GitHub gists**,

compliant with;
<ul>
  <li><a href="https://jsonresume.org/schema">JSONResume.org/schema</a></li>
  <li><a href="https://json-schema.org">JSON-Schema.org</a></li>
</ul>

<details>
  <summary><b>JSONResume</b></summary>

> #### What is a JSONResume?
> A community driven open source initiative to create a JSON based standard for resumes

> #### Why JSON?
> It's lightweight, easy to use and it's perfect to build tools for!
> JSON Schema is mature enough for writing usable semantics.

##### read more

<ul>
  <li><a href="https://jsonresume.org">jsonresume.org</a></li>
  <li><a href="https://github.com/jsonresume">git:jsonresume</a></li>
  <li><a href="https://github.com/jsonresume/resume-schema">git:resume-schema</a></li>
</ul>

Checkout [Basic example](#basic-example)

</details>

<hr>

Along with headless [puppeteer](https://pptr.dev) integration for exporting PDF files.

---

## Why

Have you spent countless hours making a resume only to end up having to redo it when you want to change the format?
what json resume does is allow for you to input your data in one place and then dynamically generate your resume with different templates

---

## How

Reads `resume.json` from one of the following methods:

- [public-gists](#public-gists)
- [secret-gists](#secret-gists)

---

## Usage

#### Public Gists

#### `<HOST>/user/<username>`

> [!IMPORTANT]
> the `<username>` is GitHub username

> [!CAUTION]
> the user **MUST** have a **public** gist with `resume.json` file

> [!NOTE]
>
> eg;
>
> `<username>`
> <kbd>DrakeAxelrod</kbd>
>
> <sup><sub>[gist.github.com/DrakeAxelrod/33726f328fa7d66f781f6408aac9c20e](https://gist.github.com/DrakeAxelrod/33726f328fa7d66f781f6408aac9c20e)</sup></sub>
>
> <sup><sub>[json-resume-service.vercel.app/user/drakeaxelrod](https://json-resume-service.vercel.app/user/drakeaxelrod)</sup></sub>

---

#### Secret Gists

#### `<HOST>/gist/<gist_id>`

> [!IMPORTANT]
>
> the `<gist_id>` is the secret gist id

> [!CAUTION]
> the user **MUST** have a compliant **JSON** file in given gist

> [!TIP]
>
> the **first JSON** file in that gist will be attempted
>
> the file can be named anything
>
> eg; `my-private.json`


> [!NOTE]
>
> eg;
>
> `<gist_id>`
> <kbd>6776c2096963f1ca8ddb1817c8674b93</kbd>
>
> <sup><sub>[gist.github.com/metaory/6776c2096963f1ca8ddb1817c8674b93](https://gist.github.com/metaory/6776c2096963f1ca8ddb1817c8674b93)</sup></sub>
>
> <sup><sub>[json-resume-service.vercel.app/gist/6776c2096963f1ca8ddb1817c8674b93](https://json-resume-service.vercel.app/gist/6776c2096963f1ca8ddb1817c8674b93)</sup></sub>

---

## Development

You'll want to fork this repository and deploy your own resume generator service.

1. [Fork](https://github.com/DrakeAxelrod/json-resume-service/fork) this repository

2. Clone your fork

```sh
git clone https://github.com/<YOUR_USERNAME>/json-resume-service.git
# or
git YOUR_USERNAME>/json-resume-service.git
```

3. Navigate to cloned repository

```sh
cd json-resume-service
```

4. Install local dependencies

```sh
npm i
# or
pnpm install
```

5. Run locally

```sh
pnpm dev
# or
npm run dev
```

6. Visit [localhost:3000](http://localhost:3000)

- Public route [localhost:3000/user/`<username>`](localhost:3000/user/<username>)
- Secret route [localhost:3000/gist/`<gist_id>`](localhost:3000/gist/<gist_id>)

Replace `<username>` or `<gist_id>` accordingly


7. (OPTIONALLY) Deploy to the cloud by running going to [Vercel](https://vercel.com/) and making an account if you don't have one or you another hosting service of your choice.

---

### Basic example

A basic example from _[jsonresume.org/schema](https://jsonresume.org/schema)_

<details>
  <summary>basic <kbd>resume.json</kbd></summary>

```json
{
  "basics": {
    "name": "John Doe",
    "label": "Programmer",
    "image": "",
    "email": "john@gmail.com",
    "phone": "(912) 555-4321",
    "url": "https://johndoe.com",
    "summary": "A summary of John Doe…",
    "location": {
      "address": "2712 Broadway St",
      "postalCode": "CA 94115",
      "city": "San Francisco",
      "countryCode": "US",
      "region": "California"
    },
    "profiles": [{
      "network": "Twitter",
      "username": "john",
      "url": "https://twitter.com/john"
    }]
  },
  "work": [{
    "name": "Company",
    "position": "President",
    "url": "https://company.com",
    "startDate": "2013-01-01",
    "endDate": "2014-01-01",
    "summary": "Description…",
    "highlights": [
      "Started the company"
    ]
  }],
  "volunteer": [{
    "organization": "Organization",
    "position": "Volunteer",
    "url": "https://organization.com/",
    "startDate": "2012-01-01",
    "endDate": "2013-01-01",
    "summary": "Description…",
    "highlights": [
      "Awarded 'Volunteer of the Month'"
    ]
  }],
  "education": [{
    "institution": "University",
    "url": "https://institution.com/",
    "area": "Software Development",
    "studyType": "Bachelor",
    "startDate": "2011-01-01",
    "endDate": "2013-01-01",
    "score": "4.0",
    "courses": [
      "DB1101 - Basic SQL"
    ]
  }],
  "awards": [{
    "title": "Award",
    "date": "2014-11-01",
    "awarder": "Company",
    "summary": "There is no spoon."
  }],
  "certificates": [{
    "name": "Certificate",
    "date": "2021-11-07",
    "issuer": "Company",
    "url": "https://certificate.com"
  }],
  "publications": [{
    "name": "Publication",
    "publisher": "Company",
    "releaseDate": "2014-10-01",
    "url": "https://publication.com",
    "summary": "Description…"
  }],
  "skills": [{
    "name": "Web Development",
    "level": "Master",
    "keywords": [
      "HTML",
      "CSS",
      "JavaScript"
    ]
  }],
  "languages": [{
    "language": "English",
    "fluency": "Native speaker"
  }],
  "interests": [{
    "name": "Wildlife",
    "keywords": [
      "Ferrets",
      "Unicorns"
    ]
  }],
  "references": [{
    "name": "Jane Doe",
    "reference": "Reference…"
  }],
  "projects": [{
    "name": "Project",
    "startDate": "2019-01-01",
    "endDate": "2021-01-01",
    "description": "Description...",
    "highlights": [
      "Won award at AIHacks 2016"
    ],
    "url": "https://project.com/"
  }]
}
```
</details>

---

## Contributors

- [Drake Axelrod](https://github.com/drakeaxelrod)
- [metaory](https://github.com/metaory)

---

## License

Copyright © 2021-present [Drake Axelrod](https://github.com/drakeaxelrod)

[MIT](LICENSE)

---

<div align="center">
  <img width="60%" src="public/foot.svg"/>
</div>

