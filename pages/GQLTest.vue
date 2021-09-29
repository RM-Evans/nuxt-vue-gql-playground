<template>
  <div>
    <p>please do things</p>
    {{ country.name }}
    {{ country.capital }}
    {{ country.currency }}
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  //todo search for and display query
  // just need to search for country code or name of country

  apollo: {},
  //       // the client side will fetch instead. eg: maybe for use with a search engine
  prefetch: false,
}

//*just grab a json object
// export default {
//   //   data() {
//   //     return {}
//   //   },
//   apollo: {
//     country: {
//       query: gql`
//         query getCountry {
//           country(code: "US") {
//             name
//             capital
//             currency
//             languages {
//               name
//             }
//           }
//         }
//       `,
//       // the client side will fetch instead. eg: maybe for use with a search engine
//       prefetch: false,
//       update({ country }) {
//         console.log(country)
//         return country
//       },
//     },
//   },
// }
//
</script>

// country: query // //country: gql` query country { country(code: "AU") { name
capital languages { name } } } `,
