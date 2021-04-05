# Medallia Experience Cloud APIs

Medallia Experience Cloud (MEC) exposes various APIs for use by clients,
partners, integrators, and developers.  The
[Swagger-compatible](https://swagger.io/) files found in this repository
define the interface contracts for those APIs.

## URLs

Medallia's URLs are unique per instance.

Two classifications of URLs are embedded in these YAML files:

- OAuth 2.0 URLs
- API gateway URLs

The Swagger specification
[does not yet allow](https://github.com/OAI/OpenAPI-Specification/issues/551)
for using variables with OAuth 2.0 URLs.  As such, you will need to ensure
you set the OAuth 2.0 token URL prior to use.

## Usage

These YAML files are provided as supplemental material to Medallia's
[product documentation](https://docs.medallia.com).  Users are encouraged
to familiarize themselves with the details described in the documentation
prior to use.

Swagger files can assist developers with code generation and act as a
starting place for larger development efforts.  Please check all
generated code to ensure it meets your needs and perform testing to ensure
it meets the "as-built", running version on your MEC instance(s).

## License

Copyright 2021.  Medallia, Inc.

Licensed under the Apache License, Version 2.0 (the "License"); you may
not use this file except in compliance with the License.  You may obtain
a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
