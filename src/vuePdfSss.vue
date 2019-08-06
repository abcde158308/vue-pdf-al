<style src="./annotationLayer.css"></style>
<script>

	import componentFactory from './componentFactory'
	import pdfjsWrapper from './pdfjsWrapper'

	var PDFJS = pdfjsLib||PDFJSrequire('pdfjs-dist/build/pdf.js');

	if ( process.env.VUE_ENV !== 'server' ) {

		if ( typeof window !== 'undefined' && 'Worker' in window ) {

			var PdfjsWorker =PdfjsWorker || require('worker-loader!pdfjs-dist/build/pdf.worker.js');
			PDFJS.GlobalWorkerOptions.workerPort = new PdfjsWorker();
		}
	}

	var component = componentFactory(pdfjsWrapper(PDFJS));
	component.PDFJS = PDFJS;

	export default component;

</script>